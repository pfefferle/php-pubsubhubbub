## Publisher

A simple "publisher" demo:

```php
include("publisher.php");

$hub_url = "http://pubsubhubbub.appspot.com";
$topic_url = "http://notizblog.org/feed/";
    
// check that a hub url is specified
    if (!$hub_url) {
        echo "Please specify a hub url.<br /><br /><a href='publisher_example.php'>back</a>";
        exit();
    }
    // check that a topic url is specified
    if (!$topic_url) {
        echo "Please specify a topic url to publish.<br /><br /><a href='publisher_example.php'>back</a>";
        exit();
    }         
    
    // $hub_url = "http://pubsubhubbub.appspot.com/publish";
    $p = new Publisher($hub_url);
    if ($p->publish_update($topic_url)) {
        echo "<i>$topic_url</i> was successfully published to <i>$hub_url</i><br /><br /><a href='publisher_example.php'>back</a>";
    } else {
        echo "ooops...";
        print_r($p->last_response());
    }
```

## Subscriber

A simple "subscriber" demo:

```php
include("subscriber.php");

$hub_url = "http://pubsubhubbub.appspot.com";
$callback_url = "put your own endpoint here";

$feed = "http://notizblog.org/feed/";

// create a new subscriber
$s = new Subscriber($hub_url, $callback_url);

// subscribe to a feed
$s->subscribe($feed);

// unsubscribe from a feed
$s->unsubscribe($feed);
```