# simpleIG 
Instagram account content on your site.

## Getting Started

Load **simpleIG.php** or use function directly.  You need instagram account name and number of posts (default 5 newest).

```
function instagram($username = "instagram", $number = 5) {
        $source = file_get_contents('http://instagram.com/'.$username);
        $shrd = explode('window._sharedData = ', $source);
        $json = explode(';</script>', $shrd[1]);
        $insta_data = json_decode($json[0], TRUE);
        $data = array();
        for($item = 0; $item < $number; $item++)
        {
            array_push($data,$insta_data['entry_data']['ProfilePage'][0]["graphql"]['user']["edge_owner_to_timeline_media"] ["edges"][$item]["node"]);
        }
        return $data;
    }
```

## Returned data

![enter image description here](http://www.marianmzigot.com/git/simpleIG/simpleIG.png)


