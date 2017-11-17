---
layout: post
title:      "What is the env variable in Rack?"
date:       2017-11-17 21:54:52 +0000
permalink:  what_is_the_env_variable_in_rack
---


The first time looked at the call method in Rack there is a parameter/variable called env. What is it? 
It is a hash. Rack and other middlewares can add values to it. 
Here is an example of env variable:
{
  "GATEWAY_INTERFACE" => "CGI/1.1",
  "PATH_INFO" => "/index.html",
  "QUERY_STRING" => "",
  "REMOTE_ADDR" => "::1",
  "REMOTE_HOST" => "localhost",
  "REQUEST_METHOD" => "GET",
  "REQUEST_URI" => "http://localhost:3000/index.html",
  "SCRIPT_NAME" => "",
  "SERVER_NAME" => "localhost",
  "SERVER_PORT" => "3000",
  "SERVER_PROTOCOL" => "HTTP/1.1",
  "SERVER_SOFTWARE" => "WEBrick/1.3.1 (Ruby/2.0.0/2013-11-22)",
  "HTTP_HOST" => "localhost:3000",
  "HTTP_USER_AGENT" => "Mozilla/5.0 (Macintosh; Intel Mac OS X 10.9; rv:26.0) Gecko/20100101 Firefox/26.0",
  "HTTP_ACCEPT" => "text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8",
  "HTTP_ACCEPT_LANGUAGE" => "zh-tw,zh;q=0.8,en-us;q=0.5,en;q=0.3",
  "HTTP_ACCEPT_ENCODING" => "gzip, deflate",
  "HTTP_COOKIE" => "jsonrpc.session=3iqp3ydRwFyqjcfO0GT2bzUh.bacc2786c7a81df0d0e950bec8fa1a9b1ba0bb61",
  "HTTP_CONNECTION" => "keep-alive",
  "HTTP_CACHE_CONTROL" => "max-age=0",
  "rack.version" => [1, 2],
  "rack.input" => #<StringIO:0x007fa1bce039f8>,
  "rack.errors" => #<IO:<STDERR>>,
  "rack.multithread" => true,
  "rack.multiprocess" => false,
  "rack.run_once" => false,
  "rack.url_scheme" => "http",
  "HTTP_VERSION" => "HTTP/1.1",
  "REQUEST_PATH" => "/index.html"
}

These keys in string seem complicated. But let's take a deep look. There are 3 categories of keys. Rack uses a simple convention for these keys: request headers, server_info and Rack_info.

All headers that have been part of the actual HTTP request are prefixed with HTTP and uppercased. 

All other uppercase keys represent additional information that has been passed (added) from the webserver that has received the request (in this case WEBrick, which runs our little Rack application). 

All keys that are prefixed with rack. represent internal additions that Rack adds.
