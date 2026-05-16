---
title: "HTTP Status Codes — Quick Reference Guide"
date: 2025-05-16
description: "Complete HTTP status code reference. Searchable list with descriptions, use cases, and color-coded categories. Quick lookup for 1xx to 5xx status codes."
categories: ["Free Tools"]
slug: "http-status-codes"
ShowToc: false
aliases:
  - "/tools/http-status-codes/"
  - "/tools/http-status-codes/"
cover:
  image: "/images/covers/http-status-codes.png"
  alt: "HTTP Status Codes Reference"
---

<div id="http-app">

<style>
#http-app {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
  max-width: 900px;
  margin: 0 auto;
  padding: 0 16px 48px;
  color: #1a1a2e;
}

/* ── Controls ── */
#http-app .hsc-controls {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  margin-bottom: 24px;
}

#http-app .hsc-search {
  flex: 1 1 220px;
  padding: 10px 14px;
  border: 2px solid #d1d5db;
  border-radius: 8px;
  font-size: 15px;
  outline: none;
  transition: border-color 0.2s;
}
#http-app .hsc-search:focus {
  border-color: #4f46e5;
}

#http-app .hsc-filter-group {
  display: flex;
  flex-wrap: wrap;
  gap: 6px;
}

#http-app .hsc-filter-btn {
  padding: 8px 14px;
  border: 2px solid transparent;
  border-radius: 20px;
  font-size: 13px;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.18s;
  background: #f3f4f6;
  color: #374151;
}
#http-app .hsc-filter-btn:hover,
#http-app .hsc-filter-btn.active {
  color: #fff;
}
#http-app .hsc-filter-btn[data-cat="all"].active  { background: #4f46e5; }
#http-app .hsc-filter-btn[data-cat="1xx"].active  { background: #6366f1; }
#http-app .hsc-filter-btn[data-cat="2xx"].active  { background: #16a34a; }
#http-app .hsc-filter-btn[data-cat="3xx"].active  { background: #d97706; }
#http-app .hsc-filter-btn[data-cat="4xx"].active  { background: #dc2626; }
#http-app .hsc-filter-btn[data-cat="5xx"].active  { background: #7c3aed; }

/* ── Result count ── */
#http-app .hsc-count {
  font-size: 13px;
  color: #6b7280;
  margin-bottom: 16px;
}

/* ── Category heading ── */
#http-app .hsc-cat-heading {
  display: flex;
  align-items: center;
  gap: 10px;
  margin: 28px 0 10px;
  font-size: 18px;
  font-weight: 700;
}
#http-app .hsc-cat-badge {
  display: inline-block;
  padding: 3px 12px;
  border-radius: 12px;
  font-size: 13px;
  font-weight: 700;
  color: #fff;
}
#http-app .hsc-cat-badge.c1xx { background: #6366f1; }
#http-app .hsc-cat-badge.c2xx { background: #16a34a; }
#http-app .hsc-cat-badge.c3xx { background: #d97706; }
#http-app .hsc-cat-badge.c4xx { background: #dc2626; }
#http-app .hsc-cat-badge.c5xx { background: #7c3aed; }

/* ── Code cards ── */
#http-app .hsc-card {
  border-radius: 10px;
  border: 1.5px solid #e5e7eb;
  margin-bottom: 8px;
  overflow: hidden;
  transition: box-shadow 0.18s;
}
#http-app .hsc-card:hover {
  box-shadow: 0 2px 10px rgba(0,0,0,0.09);
}
#http-app .hsc-card.common {
  border-width: 2px;
}
#http-app .hsc-card.c1xx.common { border-color: #6366f1; }
#http-app .hsc-card.c2xx.common { border-color: #16a34a; }
#http-app .hsc-card.c3xx.common { border-color: #d97706; }
#http-app .hsc-card.c4xx.common { border-color: #dc2626; }
#http-app .hsc-card.c5xx.common { border-color: #7c3aed; }

#http-app .hsc-card-header {
  display: flex;
  align-items: center;
  gap: 12px;
  padding: 12px 16px;
  cursor: pointer;
  user-select: none;
  background: #fff;
}
#http-app .hsc-card-header:hover {
  background: #f9fafb;
}

#http-app .hsc-code-num {
  font-size: 20px;
  font-weight: 800;
  min-width: 56px;
  text-align: center;
  padding: 4px 8px;
  border-radius: 6px;
  color: #fff;
  letter-spacing: -0.5px;
}
#http-app .hsc-code-num.c1xx { background: #6366f1; }
#http-app .hsc-code-num.c2xx { background: #16a34a; }
#http-app .hsc-code-num.c3xx { background: #d97706; }
#http-app .hsc-code-num.c4xx { background: #dc2626; }
#http-app .hsc-code-num.c5xx { background: #7c3aed; }

#http-app .hsc-card-meta {
  flex: 1;
  min-width: 0;
}
#http-app .hsc-code-name {
  font-size: 15px;
  font-weight: 700;
  color: #111827;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}
#http-app .hsc-code-desc {
  font-size: 13px;
  color: #6b7280;
  margin-top: 2px;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}

#http-app .hsc-common-star {
  font-size: 11px;
  font-weight: 700;
  color: #fff;
  background: #f59e0b;
  padding: 2px 7px;
  border-radius: 10px;
  white-space: nowrap;
  flex-shrink: 0;
}

#http-app .hsc-copy-btn {
  flex-shrink: 0;
  padding: 6px 12px;
  border: 1.5px solid #d1d5db;
  border-radius: 6px;
  font-size: 12px;
  font-weight: 600;
  background: #fff;
  color: #374151;
  cursor: pointer;
  transition: all 0.15s;
}
#http-app .hsc-copy-btn:hover {
  background: #4f46e5;
  color: #fff;
  border-color: #4f46e5;
}
#http-app .hsc-copy-btn.copied {
  background: #16a34a;
  color: #fff;
  border-color: #16a34a;
}

#http-app .hsc-chevron {
  flex-shrink: 0;
  width: 20px;
  height: 20px;
  color: #9ca3af;
  transition: transform 0.2s;
}
#http-app .hsc-card.open .hsc-chevron {
  transform: rotate(180deg);
}

/* ── Expanded detail ── */
#http-app .hsc-detail {
  display: none;
  padding: 14px 20px 18px;
  border-top: 1px solid #e5e7eb;
  background: #f9fafb;
  font-size: 14px;
  line-height: 1.7;
  color: #374151;
}
#http-app .hsc-card.open .hsc-detail {
  display: block;
}

#http-app .hsc-detail h4 {
  margin: 0 0 6px;
  font-size: 13px;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  color: #6b7280;
}
#http-app .hsc-detail p {
  margin: 0 0 12px;
}
#http-app .hsc-detail .hsc-usecase {
  background: #fff;
  border: 1px solid #e5e7eb;
  border-radius: 6px;
  padding: 10px 14px;
  font-size: 13px;
  color: #374151;
}

/* ── No results ── */
#http-app .hsc-no-results {
  text-align: center;
  padding: 48px 0;
  color: #9ca3af;
  font-size: 16px;
  display: none;
}

/* ── Mobile ── */
@media (max-width: 600px) {
  #http-app .hsc-code-desc { display: none; }
  #http-app .hsc-copy-btn { display: none; }
}
</style>

<!-- Controls -->
<div class="hsc-controls">
  <input
    id="hscSearch"
    class="hsc-search"
    type="search"
    placeholder="Search by code number or keyword… e.g. 404 or not found"
    aria-label="Search HTTP status codes"
  />
  <div class="hsc-filter-group" role="group" aria-label="Filter by category">
    <button class="hsc-filter-btn active" data-cat="all">All</button>
    <button class="hsc-filter-btn" data-cat="1xx">1xx Info</button>
    <button class="hsc-filter-btn" data-cat="2xx">2xx Success</button>
    <button class="hsc-filter-btn" data-cat="3xx">3xx Redirect</button>
    <button class="hsc-filter-btn" data-cat="4xx">4xx Client Error</button>
    <button class="hsc-filter-btn" data-cat="5xx">5xx Server Error</button>
  </div>
</div>

<div id="hscCount" class="hsc-count"></div>

<!-- Code list rendered by JS -->
<div id="hscList"></div>
<div id="hscNoResults" class="hsc-no-results">No status codes match your search.</div>

<script>
(function () {
  var COMMON = [200,201,301,302,400,401,403,404,500,502,503];

  var CODES = [
    /* ── 1xx ── */
    {
      code: 100, name: "Continue",
      desc: "The server has received the request headers.",
      detail: "Indicates that the client should continue with its request. This interim response tells the client that the initial part of the request has been received and the client should proceed with the rest of the request, or ignore this response if the request was already completed.",
      usecase: "Used when a client sends a request with an Expect: 100-continue header before sending a large request body. The server responds 100 to signal it's ready to accept the body."
    },
    {
      code: 101, name: "Switching Protocols",
      desc: "The server agrees to switch protocols.",
      detail: "Sent in response to an Upgrade request header from the client, indicating the protocol the server is switching to. The server will switch protocols immediately after the blank line following this response.",
      usecase: "Used when upgrading an HTTP connection to WebSocket (Upgrade: websocket header). The server sends 101 to confirm the protocol switch."
    },
    {
      code: 102, name: "Processing",
      desc: "The server has received and is processing the request.",
      detail: "A WebDAV response code indicating that the server has received and is processing the request, but no response is available yet. This prevents the client from timing out while the server works on a long-running operation.",
      usecase: "WebDAV operations that take more than a few seconds to complete, preventing client timeout."
    },
    {
      code: 103, name: "Early Hints",
      desc: "Used to return some response headers before final response.",
      detail: "Allows the server to send preliminary HTTP headers before the final HTTP message. Primarily used with the Link header to allow browsers to preload resources while the server prepares a response.",
      usecase: "Server sends Link headers for CSS/JS files while still generating the main HTML response, allowing the browser to start preloading assets sooner."
    },
    /* ── 2xx ── */
    {
      code: 200, name: "OK",
      desc: "The request succeeded.",
      detail: "The standard response for successful HTTP requests. The actual response depends on the request method: GET returns the resource, POST returns the result of the action, HEAD returns only headers. The most common response code on the web.",
      usecase: "Standard successful response for GET, POST, PUT, PATCH requests. An API returning user data, or a page loading successfully."
    },
    {
      code: 201, name: "Created",
      desc: "The request succeeded and a new resource was created.",
      detail: "Indicates that a request has succeeded and a new resource has been created as a result. The response typically includes a Location header pointing to the newly created resource, and the response body may contain a representation of the new resource.",
      usecase: "REST API response after POST /users creates a new user. Location header points to /users/123."
    },
    {
      code: 202, name: "Accepted",
      desc: "The request has been received but not yet acted upon.",
      detail: "Indicates that the request has been accepted for processing, but the processing has not been completed. The request might or might not be eventually acted upon — it may be disallowed when processing occurs. Typically used for asynchronous operations.",
      usecase: "Submitting a video encoding job: the server accepts the request immediately but encoding happens in the background."
    },
    {
      code: 203, name: "Non-Authoritative Information",
      desc: "Returned metadata is not from the origin server.",
      detail: "The returned metadata is not exactly the same as available from the origin server, but is collected from a local or third-party copy. Used mainly for mirrors or backups of another resource.",
      usecase: "A proxy server returns modified headers or content from a cached copy that differs slightly from the origin."
    },
    {
      code: 204, name: "No Content",
      desc: "No content to send in the response body.",
      detail: "Indicates that the request has succeeded, but the client doesn't need to navigate away from its current page. Often used after a DELETE request, or when updating a resource via PUT/PATCH where no body is needed in the response.",
      usecase: "DELETE /items/42 succeeds — the server returns 204 with no body. Also used for auto-save operations where the UI doesn't need to update."
    },
    {
      code: 205, name: "Reset Content",
      desc: "Reset the document view that sent this request.",
      detail: "Tells the client to reset the document which sent the request. Similar to 204 No Content but requires the requester to reset the document view, for example clearing a form after submission.",
      usecase: "After a form submission, instructs the browser to clear the form fields so the user can enter new data."
    },
    {
      code: 206, name: "Partial Content",
      desc: "Partial content delivered due to a range request.",
      detail: "Used when the client sends a Range header to request only part of a resource. The response must include a Content-Range header indicating the range delivered. Enables resumable downloads and video streaming.",
      usecase: "Streaming video: the player requests bytes 0–1048575 via Range: bytes=0-1048575. The server responds 206 with that chunk."
    },
    {
      code: 207, name: "Multi-Status",
      desc: "Conveys information about multiple resources (WebDAV).",
      detail: "A WebDAV response that conveys information about multiple resources, for situations where multiple status codes might be appropriate. The response body is an XML document with individual status codes for each resource.",
      usecase: "WebDAV PROPFIND or COPY operations that affect multiple resources, each with its own success/failure status."
    },
    {
      code: 208, name: "Already Reported",
      desc: "Members of a DAV binding already enumerated (WebDAV).",
      detail: "Used inside a DAV: propstat response element to avoid enumerating the internal members of multiple bindings to the same collection repeatedly.",
      usecase: "WebDAV: prevents infinite loops when a collection contains circular references."
    },
    {
      code: 226, name: "IM Used",
      desc: "The server fulfilled a GET request for the resource using delta encoding.",
      detail: "The server has fulfilled a GET request for the resource, and the response is a representation of the result of one or more instance-manipulations applied to the current instance. Used with HTTP delta encoding.",
      usecase: "Delta encoding: the server sends only the changes (diff) from the previously cached version of a resource."
    },
    /* ── 3xx ── */
    {
      code: 300, name: "Multiple Choices",
      desc: "The request has more than one possible response.",
      detail: "Indicates that the request has more than one possible response. The user-agent or user should choose one of them. There is no standardized way to choose automatically, though the server may indicate a preferred choice.",
      usecase: "A resource available in multiple formats (HTML, JSON, XML) — the server presents choices and the client picks one."
    },
    {
      code: 301, name: "Moved Permanently",
      desc: "The URL of the requested resource has changed permanently.",
      detail: "Indicates that the resource has been permanently moved to a new URL. Search engines update their links to use the new URL. Browsers cache this redirect. By convention, the new URL is provided in the Location header. GET method may be changed to GET on redirect.",
      usecase: "Redirecting HTTP to HTTPS, or a website changing its domain. Old URLs pass their SEO value to the new URL."
    },
    {
      code: 302, name: "Found",
      desc: "The URL has been changed temporarily.",
      detail: "Indicates that the resource is found at another URI temporarily. The client should continue to use the original URI. Browsers follow the redirect but don't cache it permanently. Often misused; 307 is preferred when the method must not change.",
      usecase: "Post/Redirect/Get pattern: after a form POST succeeds, redirect to a results page so refresh doesn't resubmit the form."
    },
    {
      code: 303, name: "See Other",
      desc: "Redirects to another page, always using GET.",
      detail: "Indicates that the redirects don't link to the requested resource itself, but to another page (such as a confirmation page). Unlike 302, always triggers a GET on the new URL regardless of the original method.",
      usecase: "After a POST form submission creates a resource, redirect the browser to a GET page showing the new resource."
    },
    {
      code: 304, name: "Not Modified",
      desc: "Tells the client the response has not been modified.",
      detail: "Used for caching. Tells the client that the response has not been modified, so the client can use the same cached version it already has. The response must not contain a body — just headers. Triggered by conditional requests using If-None-Match or If-Modified-Since.",
      usecase: "Browser sends If-None-Match: \"abc123\" with an ETag. Server confirms the resource hasn't changed — client uses its cached copy."
    },
    {
      code: 307, name: "Temporary Redirect",
      desc: "Temporary redirect; method must not change.",
      detail: "Similar to 302 Found, but guarantees that the method and body will not be changed when the redirected request is made. If a POST is redirected, the new request will also be POST. Use when you need to preserve the HTTP method.",
      usecase: "Temporarily routing an API POST endpoint to a different server during maintenance while preserving the POST method."
    },
    {
      code: 308, name: "Permanent Redirect",
      desc: "Permanent redirect; method must not change.",
      detail: "Similar to 301 Moved Permanently, but guarantees that the method and body will not be changed. Search engines update their links, browsers cache permanently, and the HTTP method is preserved. The permanent equivalent of 307.",
      usecase: "Permanently moving an API endpoint from /v1/users to /v2/users while ensuring clients still send POST (not GET)."
    },
    /* ── 4xx ── */
    {
      code: 400, name: "Bad Request",
      desc: "The server cannot process the request due to client error.",
      detail: "The server cannot or will not process the request due to something perceived as a client error — malformed request syntax, invalid request message framing, or deceptive request routing. The client should not repeat the request without modification.",
      usecase: "Missing required fields in an API request body, malformed JSON, invalid query parameter types."
    },
    {
      code: 401, name: "Unauthorized",
      desc: "Authentication is required and has not been provided.",
      detail: "Although named 'Unauthorized', this code means 'unauthenticated'. The client must authenticate itself to get the requested response. The response must include a WWW-Authenticate header with a challenge applicable to the requested resource.",
      usecase: "Accessing a protected API endpoint without an Authorization header or with an invalid/expired token."
    },
    {
      code: 402, name: "Payment Required",
      desc: "Reserved for future use; sometimes used for rate limits.",
      detail: "Originally intended for digital payment systems. The specification is vague, and the code is rarely used. Some APIs use it to indicate a subscription is required or a payment wall has been hit.",
      usecase: "Some SaaS APIs return 402 when a free-tier quota is exceeded and a paid plan is required."
    },
    {
      code: 403, name: "Forbidden",
      desc: "The server refuses to authorize the request.",
      detail: "The client's identity is known but it does not have access rights to the content. Unlike 401, re-authenticating will make no difference. The server understood the request but refuses to authorize it.",
      usecase: "A logged-in user trying to access admin-only pages. Or accessing another user's private data."
    },
    {
      code: 404, name: "Not Found",
      desc: "The server cannot find the requested resource.",
      detail: "The server cannot find the requested resource. This can mean the URL is wrong, the resource never existed, or the resource has been deleted. Often used as a catch-all for resources that don't exist. Servers may return 404 to hide the existence of a resource from unauthorized clients (vs. 403).",
      usecase: "Requesting a blog post that was deleted, a user ID that doesn't exist, or mistyping a URL."
    },
    {
      code: 405, name: "Method Not Allowed",
      desc: "The request method is not supported.",
      detail: "The request method is known by the server but is not supported by the target resource. The server must include an Allow header listing the supported methods. For example, a read-only resource rejects DELETE requests.",
      usecase: "Sending a DELETE request to an endpoint that only supports GET and POST."
    },
    {
      code: 406, name: "Not Acceptable",
      desc: "No content matching the Accept headers was found.",
      detail: "Indicates that the server cannot produce a response matching the Accept headers sent in the request. For example, the client only accepts application/json but the server only supports text/xml.",
      usecase: "Client sends Accept: application/json but the server only serves XML for that resource."
    },
    {
      code: 407, name: "Proxy Authentication Required",
      desc: "Authentication with the proxy is required.",
      detail: "Similar to 401, but authentication needs to be done by a proxy. The proxy must return a Proxy-Authenticate header for the client to authenticate with.",
      usecase: "Corporate environments where HTTP traffic must authenticate through an intermediate proxy server."
    },
    {
      code: 408, name: "Request Timeout",
      desc: "The server timed out waiting for the request.",
      detail: "Sent by some servers when an idle connection is shut down. This indicates the server would like to close this unused connection. Used heavily by some servers like Apache.",
      usecase: "A slow client took too long to send the request body. The server closes the connection after its idle timeout."
    },
    {
      code: 409, name: "Conflict",
      desc: "The request conflicts with the current state of the resource.",
      detail: "Indicates that the request conflicts with the current state of the server. Most likely with PUT requests where multiple requests are editing a resource simultaneously. The response body should describe the conflict.",
      usecase: "Trying to create a user with an email that already exists. Or a version conflict in an optimistic-locking system."
    },
    {
      code: 410, name: "Gone",
      desc: "The resource is permanently deleted and will not return.",
      detail: "Indicates that access to the target resource is no longer available and that this condition is likely to be permanent. Unlike 404, this indicates intentional, permanent removal. Useful to signal search engines to deindex the URL.",
      usecase: "A product that has been discontinued. Sending 410 tells search engines to remove the URL from their index."
    },
    {
      code: 411, name: "Length Required",
      desc: "Content-Length header is required.",
      detail: "The server refuses to accept the request without a defined Content-Length header. The client may repeat the request if it adds a valid Content-Length header.",
      usecase: "Sending a POST request without a Content-Length header to a server that requires it."
    },
    {
      code: 412, name: "Precondition Failed",
      desc: "Access to the resource has been denied.",
      detail: "The client has indicated preconditions in its headers which the server does not meet. Used in conditional requests with If-Match, If-None-Match, If-Modified-Since, If-Unmodified-Since headers.",
      usecase: "Optimistic concurrency: client sends If-Match: \"old-etag\" to update a resource, but the resource has already been modified by someone else."
    },
    {
      code: 413, name: "Content Too Large",
      desc: "The request body is larger than the server will accept.",
      detail: "The request entity is larger than limits defined by the server. The server might close the connection or return a Retry-After header if the situation is temporary.",
      usecase: "Uploading a file that exceeds the server's maximum allowed upload size (e.g., an image over 10MB)."
    },
    {
      code: 414, name: "URI Too Long",
      desc: "The URI requested is longer than the server will process.",
      detail: "The URI provided was too long for the server to process. This can occur when a client converts a POST request to a GET request with a long query string.",
      usecase: "A search query or filter with thousands of characters in the URL query string."
    },
    {
      code: 415, name: "Unsupported Media Type",
      desc: "The request media type is not supported.",
      detail: "The media format of the requested data is not supported by the server, so the server is rejecting the request. Typically triggered when the Content-Type header doesn't match what the server expects.",
      usecase: "Sending text/plain to an API endpoint that only accepts application/json."
    },
    {
      code: 416, name: "Range Not Satisfiable",
      desc: "The requested range cannot be fulfilled.",
      detail: "The range specified by the Range header field in the request cannot be fulfilled. The range might be outside the size of the target URI's data. The response includes a Content-Range header with an asterisk (*) indicating the actual size.",
      usecase: "Client requests bytes 9000-9999 of a 5000-byte file — the range is beyond the file's end."
    },
    {
      code: 417, name: "Expectation Failed",
      desc: "The expectation in the Expect header cannot be met.",
      detail: "The expectation indicated by the Expect request-header field cannot be met by the server.",
      usecase: "Client sends Expect: 100-continue but the server cannot fulfill the expectation (e.g., request body too large)."
    },
    {
      code: 418, name: "I'm a Teapot",
      desc: "The server refuses to brew coffee because it is a teapot.",
      detail: "An April Fools' joke from 1998 (RFC 2324, Hyper Text Coffee Pot Control Protocol). Any attempt to brew coffee with a teapot should result in this error code. It is not expected to be implemented by actual HTTP servers. Kept as a joke in the HTTP spec.",
      usecase: "Easter eggs in APIs and developer tools. Google returns 418 at https://www.google.com/teapot."
    },
    {
      code: 422, name: "Unprocessable Content",
      desc: "The request is well-formed but has semantic errors.",
      detail: "The server understands the content type of the request entity and the syntax is correct but was unable to process the contained instructions. Commonly used by REST APIs to indicate validation failures — the JSON is valid, but the data violates business rules.",
      usecase: "Valid JSON body but a field fails validation: age: -5 or email: 'not-an-email'."
    },
    {
      code: 423, name: "Locked",
      desc: "The resource that is being accessed is locked (WebDAV).",
      detail: "The resource that is being accessed is locked. WebDAV response for when a resource is locked and cannot be modified.",
      usecase: "WebDAV: a document checked out by another user cannot be modified."
    },
    {
      code: 424, name: "Failed Dependency",
      desc: "The request failed because it depended on a failed request (WebDAV).",
      detail: "The method could not be performed on the resource because the requested action depended on another action which failed (WebDAV).",
      usecase: "WebDAV batch operations where a prior operation in the batch failed."
    },
    {
      code: 425, name: "Too Early",
      desc: "The server is unwilling to risk processing a replayed request.",
      detail: "Indicates that the server is unwilling to risk processing a request that might be replayed. Used to prevent replay attacks in TLS early data (0-RTT).",
      usecase: "TLS 1.3 early data: the server declines to process a request sent in the TLS handshake to prevent replay attacks."
    },
    {
      code: 426, name: "Upgrade Required",
      desc: "The client should switch to a different protocol.",
      detail: "The server refuses to perform the request using the current protocol but will be willing to do so after the client upgrades to a different protocol. The server must include an Upgrade header indicating the required protocol.",
      usecase: "Server requires the client to upgrade from HTTP/1.1 to HTTP/2 or from HTTP to HTTPS."
    },
    {
      code: 428, name: "Precondition Required",
      desc: "The origin server requires the request to be conditional.",
      detail: "Indicates that the origin server requires the request to be conditional. This response is meant to prevent the 'lost update' problem where a client GETs a resource's state, modifies it, and PUTs it back, but a third party has modified the state in between.",
      usecase: "API requires If-Match or If-Unmodified-Since headers on update requests to prevent conflicting concurrent updates."
    },
    {
      code: 429, name: "Too Many Requests",
      desc: "The user has sent too many requests (rate limiting).",
      detail: "Indicates the user has sent too many requests in a given amount of time. The response may include a Retry-After header indicating how long the client should wait before making a new request. Fundamental to API rate limiting.",
      usecase: "API rate limiting: a client exceeds 100 requests per minute. The server responds 429 with Retry-After: 30."
    },
    {
      code: 431, name: "Request Header Fields Too Large",
      desc: "The request's HTTP headers are too large.",
      detail: "The server is unwilling to process the request because its header fields are too large. The request may be resubmitted after reducing the size of the request header fields. Often caused by excessively large cookies.",
      usecase: "Too many or too large cookies accumulated over time cause the request headers to exceed the server limit."
    },
    {
      code: 451, name: "Unavailable For Legal Reasons",
      desc: "The resource is unavailable due to legal demands.",
      detail: "The user requested a resource that cannot legally be provided. The response should include a Link header with a rel=blocked-by linking to the entity that imposed the restriction. Named after Fahrenheit 451.",
      usecase: "Content blocked in a specific country due to copyright law, court orders, or government regulations."
    },
    /* ── 5xx ── */
    {
      code: 500, name: "Internal Server Error",
      desc: "The server encountered an unexpected condition.",
      detail: "A generic error message given when an unexpected condition was encountered and no more specific message is suitable. The server encountered an error it didn't know how to handle. It is a catch-all response for server-side errors.",
      usecase: "An unhandled exception in server code, a database query that throws an error, or a misconfigured server."
    },
    {
      code: 501, name: "Not Implemented",
      desc: "The server does not support the request method.",
      detail: "The server does not support the functionality required to fulfill the request. This is the appropriate response when the server does not recognize the request method and is not capable of supporting it for any resource.",
      usecase: "A server that only implements GET and POST returns 501 when it receives a PATCH request it doesn't support."
    },
    {
      code: 502, name: "Bad Gateway",
      desc: "The server got an invalid response from an upstream server.",
      detail: "The server, while acting as a gateway or proxy, received an invalid response from an upstream server it accessed in attempting to fulfill the request. The upstream server is the problem, not the proxy itself.",
      usecase: "A reverse proxy (Nginx) cannot reach the application server (Node.js), or the application server crashes and returns garbage."
    },
    {
      code: 503, name: "Service Unavailable",
      desc: "The server is not ready to handle the request.",
      detail: "The server is not ready to handle the request. Common causes include a server that is down for maintenance or that is overloaded. A Retry-After header should be included if the service is temporarily unavailable.",
      usecase: "Server under maintenance, database connection pool exhausted, or autoscaling hasn't kicked in yet during a traffic spike."
    },
    {
      code: 504, name: "Gateway Timeout",
      desc: "The gateway timed out waiting for an upstream server.",
      detail: "The server, while acting as a gateway or proxy, did not receive a timely response from an upstream server it needed to access in order to complete the request. Different from 502 — the upstream server responded, just too slowly.",
      usecase: "A load balancer waits too long for the application server to respond (e.g., slow database query causes timeout)."
    },
    {
      code: 505, name: "HTTP Version Not Supported",
      desc: "The HTTP version used is not supported.",
      detail: "The server does not support the HTTP version used in the request. The response should contain a description of why that version is not supported and what other protocols are supported.",
      usecase: "Sending an HTTP/3 request to a server that only supports up to HTTP/1.1."
    },
    {
      code: 506, name: "Variant Also Negotiates",
      desc: "Internal server configuration error in content negotiation.",
      detail: "Transparent content negotiation for the request results in a circular reference. Indicates an internal server configuration error.",
      usecase: "Misconfigured content negotiation where a variant resource is itself configured to negotiate its content."
    },
    {
      code: 507, name: "Insufficient Storage",
      desc: "The server cannot store the representation (WebDAV).",
      detail: "The method could not be performed on the resource because the server is unable to store the representation needed to successfully complete the request. May be temporary.",
      usecase: "WebDAV: uploading a file when the server's storage quota is full."
    },
    {
      code: 508, name: "Loop Detected",
      desc: "The server detected an infinite loop (WebDAV).",
      detail: "The server terminated an operation because it encountered an infinite loop while processing a request with Depth: infinity. Used in WebDAV.",
      usecase: "WebDAV COPY or MOVE operation creates a circular directory reference."
    },
    {
      code: 510, name: "Not Extended",
      desc: "Further extensions are required for the server to fulfill the request.",
      detail: "Further extensions to the request are required for the server to fulfill it. Used with the HTTP Extension Framework (RFC 2774).",
      usecase: "An HTTP extension specified in the request is not supported by the server."
    },
    {
      code: 511, name: "Network Authentication Required",
      desc: "The client needs to authenticate to gain network access.",
      detail: "Indicates that the client needs to authenticate to gain network access. Intended for use by intercepting proxies used to control access to the network (e.g., captive portals in hotels, airports).",
      usecase: "Hotel WiFi portal: the browser is redirected to a login page. The intercepting proxy returns 511."
    }
  ];

  var CAT_CLASS = {
    "1xx": "c1xx", "2xx": "c2xx", "3xx": "c3xx", "4xx": "c4xx", "5xx": "c5xx"
  };

  function getCat(code) {
    return Math.floor(code / 100) + "xx";
  }

  function buildCard(item) {
    var cat = getCat(item.code);
    var cls = CAT_CLASS[cat];
    var isCommon = COMMON.indexOf(item.code) !== -1;
    var id = "hsc-" + item.code;

    var commonBadge = isCommon
      ? '<span class="hsc-common-star">&#9733; Common</span>'
      : "";

    return [
      '<div class="hsc-card ' + cls + (isCommon ? " common" : "") + '" data-code="' + item.code + '" data-cat="' + cat + '" id="' + id + '">',
        '<div class="hsc-card-header" onclick="hscToggle(\'' + id + '\')">',
          '<span class="hsc-code-num ' + cls + '">' + item.code + '</span>',
          '<div class="hsc-card-meta">',
            '<div class="hsc-code-name">' + item.name + '</div>',
            '<div class="hsc-code-desc">' + item.desc + '</div>',
          '</div>',
          commonBadge,
          '<button class="hsc-copy-btn" onclick="hscCopy(event, ' + item.code + ', \'' + item.name + '\')" aria-label="Copy ' + item.code + ' ' + item.name + '">Copy</button>',
          '<svg class="hsc-chevron" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><polyline points="6 9 12 15 18 9"/></svg>',
        '</div>',
        '<div class="hsc-detail">',
          '<h4>Description</h4>',
          '<p>' + item.detail + '</p>',
          '<h4>Common Use Case</h4>',
          '<div class="hsc-usecase">' + item.usecase + '</div>',
        '</div>',
      '</div>'
    ].join("");
  }

  function buildSection(cat, label, items) {
    var cls = CAT_CLASS[cat];
    var cards = items.map(buildCard).join("");
    return [
      '<div class="hsc-section" data-cat="' + cat + '">',
        '<div class="hsc-cat-heading">',
          '<span class="hsc-cat-badge ' + cls + '">' + cat.toUpperCase() + '</span>',
          label,
        '</div>',
        cards,
      '</div>'
    ].join("");
  }

  var CATEGORIES = [
    { cat: "1xx", label: "Informational" },
    { cat: "2xx", label: "Success" },
    { cat: "3xx", label: "Redirection" },
    { cat: "4xx", label: "Client Error" },
    { cat: "5xx", label: "Server Error" }
  ];

  function renderAll() {
    var list = document.getElementById("hscList");
    var html = "";
    CATEGORIES.forEach(function (catDef) {
      var items = CODES.filter(function (c) { return getCat(c.code) === catDef.cat; });
      html += buildSection(catDef.cat, catDef.label, items);
    });
    list.innerHTML = html;
  }

  function filterAndSearch(query, activeCat) {
    var q = query.toLowerCase().trim();
    var cards = document.querySelectorAll("#hscList .hsc-card");
    var sections = document.querySelectorAll("#hscList .hsc-section");
    var visible = 0;

    sections.forEach(function (sec) {
      var cat = sec.dataset.cat;
      var secVisible = 0;
      var secCards = sec.querySelectorAll(".hsc-card");
      secCards.forEach(function (card) {
        var code = card.dataset.code;
        var catMatch = activeCat === "all" || cat === activeCat;
        var item = CODES.find(function (c) { return String(c.code) === code; });
        var textMatch = !q || (
          String(item.code).indexOf(q) !== -1 ||
          item.name.toLowerCase().indexOf(q) !== -1 ||
          item.desc.toLowerCase().indexOf(q) !== -1 ||
          item.detail.toLowerCase().indexOf(q) !== -1
        );
        var show = catMatch && textMatch;
        card.style.display = show ? "" : "none";
        if (show) { secVisible++; visible++; }
      });
      sec.style.display = secVisible > 0 ? "" : "none";
    });

    document.getElementById("hscCount").textContent =
      visible + " code" + (visible !== 1 ? "s" : "") + " shown";
    document.getElementById("hscNoResults").style.display =
      visible === 0 ? "block" : "none";
  }

  window.hscToggle = function (id) {
    var card = document.getElementById(id);
    if (card) card.classList.toggle("open");
  };

  window.hscCopy = function (e, code, name) {
    e.stopPropagation();
    var text = code + " " + name;
    if (navigator.clipboard) {
      navigator.clipboard.writeText(text);
    } else {
      var ta = document.createElement("textarea");
      ta.value = text;
      document.body.appendChild(ta);
      ta.select();
      document.execCommand("copy");
      document.body.removeChild(ta);
    }
    var btn = e.currentTarget;
    btn.textContent = "Copied!";
    btn.classList.add("copied");
    setTimeout(function () {
      btn.textContent = "Copy";
      btn.classList.remove("copied");
    }, 1800);
  };

  document.addEventListener("DOMContentLoaded", function () {
    renderAll();
    filterAndSearch("", "all");

    var activeCat = "all";

    document.getElementById("hscSearch").addEventListener("input", function () {
      filterAndSearch(this.value, activeCat);
    });

    document.querySelectorAll(".hsc-filter-btn").forEach(function (btn) {
      btn.addEventListener("click", function () {
        document.querySelectorAll(".hsc-filter-btn").forEach(function (b) {
          b.classList.remove("active");
        });
        this.classList.add("active");
        activeCat = this.dataset.cat;
        filterAndSearch(document.getElementById("hscSearch").value, activeCat);
      });
    });
  });
})();
</script>

</div>

---

### Related Tools
> Test regex patterns → [Regex Tester](/tools/regex-tester/)
> Decode JWT tokens → [JWT Decoder](/tools/jwt-decoder/)
> Check IP address info → [IP Address Info](/tools/ip-address-info/)
