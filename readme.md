## Publisher

A simple "publisher" demo:

```php
include("publisher.php");

$hub_url = "http://pubsubhubbub.appspot.com";
$topic_url = "http://notizblog.org/feed/";
    
$p = new Publisher($hub_url);
if ($p->publish_update($topic_url)) {
  echo "$topic_url was successfully published to $hub_url";
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