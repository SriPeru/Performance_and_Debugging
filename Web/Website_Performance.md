# Website Performance

    1-second delay in page load time leads to

        11% fewer page views
        16% decrease in customer satisfaction
        7% loss in conversions (source: Aberdeen Group)

        Amazon and Walmart test proved this. And Akamai forun:

        47% of people expect a web page to load in two seconds or less.
        40% will abandon a web page if it takes more than three seconds to load.
        52% of online shoppers say quick page loads are important for their loyalty to a site.


## HTTP2

Use HTTP/2 to improve your web performance by more than 50%. 

That means, by enabling HTTP/2 in your exisiting website will improve 50% faster load time.


## OR use other old HTTP/1 performance improvement ideas


1. Combine and Minify Javascript and StyleSheets.

2. Make sprite images by combining images.

3. Create font icons to reduce the requests.

4. Enable Compression

    Enable Gzip compression.

        Apache: Use [mod_deflate](http://httpd.apache.org/docs/current/mod/mod_deflate.html)

        Nginx: Use (HttpGzipModule)[http://wiki.nginx.org/HttpGzipModule]
        IIS: Configure (HTTP Compression)[http://technet.microsoft.com/en-us/library/cc771003(v=WS.10).aspx]

5. Enable browser caching

#### Last-Modified
    
    Browser check with the server, if not modified "Not Modified" message will be sent to the browser. This will be faster.
    Last-modified: Fri, 16 Mar 2007 04:00:25 GMT File Contents (could be an image, HTML, CSS, Javascript...)

#### ETag

    If Server's clock is worng then the above method will fail.

    An ETag is a unique identifier given to every file, if you change the file (even by one byte), the fingerprint changes as well.

#### Expires

    Still we are checking server every time.

    Expires: Tue, 20 Mar 2007 04:00:25 GMT File Contents (could be an image, HTML, CSS, Javascript...)

    Browser checked the date and loads the cached files or downloads new files

#### Max-Age

    But it has to be computed for every date. Max-Age sets time not exact date eg "This file expires 1 week from today"

    1 day in seconds = 86400
    1 week in seconds = 604800
    1 month in seconds = 2629000
    1 year in seconds = 31536000 (effectively infinite on internet time)




### Public and Private

    Server need to controll the cache, like private data and search results etc.

    Cache-control: public
    Anyone can see it, so proxies and public servers can cache.

    Cache-control: private
    File is different for different users like Personal Homepage. This data can be cached by user's browser but not with the public proxies.

    Cache-control: no-cache
    File should not be cached, like search results.


Have a loader file (index.html) which is not cached, but that knows the locations of the items which are cached permanently. The user will always get the loader file, but may have already cached the resources it points to.

Other way of caching - Appcache / Localstorage.
