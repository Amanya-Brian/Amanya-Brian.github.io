---
layout: post
title:  "MIME Types, A brief insight"
description: "MIME types"
date:   2021-03-29 11:03:42 +0300
categories: jekyll update
---
MIME stands for Multipurpose Internet Mail Extension. It's a way of identifying files on the Internet according to their nature and format. For example, using the "Content-type" header value defined in a HTTP response, the browser can open the file with the proper extension/plugin.

## History of MIME types
MIME types were originally created for emails sent using the SMTP protocol. They did not address the issue of presentation styles. Nowadays, this standard is used in a lot of other protocols, hence the new naming convention "Internet Media Type".

## How and where are MIME types used?
A MIME type is a string identifier composed of a "type" and a "subtype". The "type" refers to a logical grouping of many MIME types that are closely related to each other. It is no more than a high level category. "subtypes" are specific to one file type within the "type".
A MIME type is a label used to identify a type of data. It is used so software can know how to handle the data. It serves the same purpose on the Internet that file extensions do on Microsoft Windows.
They are mostly found in the headers of HTTP messages (to describe the content that an HTTP server is responding with or the formatting of the data that is being POSTed in a request) and in email headers (to describe the message format and attachments).
For example, the MIME value "application/xml" is used for XML documents and specifies that the "xml" subtype belongs in the "application" type.

## Importance of MIME types
MIME types tell the browser or application what kind of data is being handled. Providing an incorrect MIME type may cause the information not to be displayed or to be displayed in a format that you would not desire. It is always good to be in control of information being sent to the browser to avoid such issues.

## Web server MIME types
There are very many MIME types for the web:
* text/html for HTML documents.
* text/plain for plain text.
* text/css for Cascading Style Sheets.
* text/javascript for JavaScript files.
* text/markdown for Markdown files.
* application/octet-stream for binary files where user action is expected.

There are also MIME types used to reference JavaScript
* application/javascript
* application/ecmascript
* application/x-ecmascript
* application/x-javascript
* text/ecmascript
* text/javascript1.0
* text/javascript1.1
* text/javascript1.2
* text/javascript1.3
* text/javascript1.4
* text/javascript1.5
* text/x-ecmascript
* text/x-javascript