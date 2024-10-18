<script id="gtm-jq-ajax-listen" type="text/javascript">
 (function() {

 'use strict';
 var $;
 var n = 0;
 init();

 function init(n) {

 // Ensure jQuery is available before anything
 if (typeof jQuery !== 'undefined') {
 
 // Define our $ shortcut locally
 $ = jQuery;
 bindToAjax();

 // Check for up to 10 seconds
 } else if (n < 20) {
 
 n++;
 setTimeout(init, 500);

 }

 }

 function bindToAjax() {

 $(document).bind('ajaxComplete', function(evt, jqXhr, opts) {

 // Create a fake a element for magically simple URL parsing
 var fullUrl = document.createElement('a');
 fullUrl.href = opts.url;

 // IE9+ strips the leading slash from a.pathname because who wants to get home on time Friday anyways
 var pathname = fullUrl.pathname[0] === '/' ? fullUrl.pathname : '/' + fullUrl.pathname;
 // Manually remove the leading question mark, if there is one
 var queryString = fullUrl.search[0] === '?' ? fullUrl.search.slice(1) : fullUrl.search;
 // Turn our params and headers into objects for easier reference
 var queryParameters = objMap(queryString, '&', '=', true);
 var headers = objMap(jqXhr.getAllResponseHeaders(), '\n', ':');

 // Blindly push to the dataLayer because this fires within GTM
 dataLayer.push({
 'event': 'ajaxComplete',
 'attributes': {
 // Return empty strings to prevent accidental inheritance of old data
 'type': opts.type || '',
 'url': fullUrl.href || '',
 'queryParameters': queryParameters,
 'pathname': pathname || '',
 'hostname': fullUrl.hostname || '',
 'protocol': fullUrl.protocol || '',
 'fragment': fullUrl.hash || '',
 'statusCode': jqXhr.status || '',
 'statusText': jqXhr.statusText || '',
 'headers': headers,
 'timestamp': evt.timeStamp || '',
 'contentType': opts.contentType || '',
 // Defer to jQuery's handling of the response
 'response': (jqXhr.responseJSON || jqXhr.responseXML || jqXhr.responseText || '')
 }
 });

 });

 }

 function objMap(data, delim, spl, decode) {

 var obj = {};

 // If one of our parameters is missing, return an empty object
 if (!data || !delim || !spl) {

 return {};

 }

 var arr = data.split(delim);
 var i;

 if (arr) {

 for (i = 0; i < arr.length; i++) {

 // If the decode flag is present, URL decode the set
 var item = decode ? decodeURIComponent(arr[i]) : arr[i];
 var pair = item.split(spl);

 var key = trim_(pair[0]);
 var value = trim_(pair[1]);

 if (key && value) {

 obj[key] = value;

 }

 }

 }

 return obj;

 }

 // Basic .trim() polyfill
 function trim_(str) {

 if (str) {

 return str.replace(/^[\s\uFEFF\xA0]+|[\s\uFEFF\xA0]+$/g, '');

 }

 }


 })();
 /*
 * v0.1.0
 * Created by the Google Analytics consultants at http://www.lunametrics.com
 * Written by @notdanwilkerson
 * Documentation: http://www.lunametrics.com/blog/2015/08/27/ajax-event-listener-google-tag-manager/
 * Licensed under the Creative Commons 4.0 Attribution Public License
 */
</script>
