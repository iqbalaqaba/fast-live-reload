# fast-live-reload
A live reload that works with all the possible browsers (ie8+)
without external dependencies (like jQuery), and can also serve
local files.

## Why

I wanted a tool where I can test small and bigger applications with
ease on different browsers, even on remote machines (see for example
[https://www.modern.ie/en-us]() ).

This tool it's specifically designed for that.

## Example
```sh
fast-live-reload
```

This will start monitoring the current folder for changes,
serving it on port 9000, and using port 9001 in order to notify
updates. Make sure the client-fast-reload.js is
loaded into your application (see Install for details):

```html
<!-- remove in production!! -->
<script type="text/javascript" src="client-fast-reload.js"></script>
```

## A More Advanced Example

```sh
fast-live-reload -s /tmp -p 8000 path1 path2 path3
```

This will monitor the given paths, listening on port 8000.

### Different Port Configuration

Since the port is different, this also needs to reflect in the client.
There are several ways to configure this.

#### 1. clientFastReloadHost Global Variable

Use the global variable `clientFastReloadHost`.

```html
<!-- remove in production!! -->
<script type="text/javascript">
    window.clientFastReloadHost="localhost:8000";
</script>
<script type="text/javascript" src="client-fast-reload.js"></script>
```

#### 2. clientFastReloadHost Query Parameter

In the URL of the page that includes the client-fast-reload.js script,
add the clientFastReloadHost query parameter.

For example:
```
http://my-site:1111/my-site/my-page.jsp?clientFastReloadHost=localhost:8000
```

You can still use other parameters if you wish. This will overwrite the
clientFastReloadHost global variable setting if it is defined.

#### 3. clientFastReloadHost Hash Parameter

In the URL of the page that includes the client-fast-reload.js script,
add the clientFastReloadHost query parameter.

For example:
```
http://my-site:1111/my-site/my-page.jsp#clientFastReloadHost=localhost:8000
```

This has the highest precedence, and will overwrite other settings.

## Install

In order to install this run:

```sh
npm install fast-live-reload
```

To fetch the client javascript, run:

```sh
bower install fast-live-reload
```

