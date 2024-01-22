# SAM INT Page Proxy
This is a temporary solution to serve the internal content of the Scout Association of Macau (SAM - INT) with HTTPS.

## Background
The internal part of the SAM website (identified by the address `http://www.scout.org.mo/INT/`) supports an obsoleted form of SSL; the old form has not been used by current browsers and is not usable. The only to access the content is to revert to `http`, and this approach is used on current SAM websites.

The adaptation of a static website (https://github.com/sam-itdc/website-static-pages/) and its generated site (https://sam-itdc.github.io/website-static-pages/) creates a new obstacle: a generated `https` website (mandatory) cannot serve `http` content. It will result in a "mix content" error. 

Although there are some workarounds to accept this mixed content error, such changes include modification to browser configuration, and it is not feasible to ask all end users to modify their browser configuration.

One approach is to establish a reverse proxy - the content by the end is served as `https` and a proxy is available to fetch the content using the old `http` method.

## Usage
For any reference to the internal site (having `http://www.scout.org.mo/INT/`), some modification is required:
- Original: `http://www.scout.org.mo/INT/api/javascript.php?key=%E4%B8%BB%E9%A1%8C%E5%B8%96%E5%85%A7%E5%AE%B92_Page%E6%97%85%E9%83%A8%E7%B0%A1%E4%BB%8B`
- Replace `http://www.scout.org.mo/INT/api/` with `https://sam-itdc-int.netlify.app/int-api/`
- https://sam-itdc-int.netlify.app/int/javascript.php?key=%E4%B8%BB%E9%A1%8C%E5%B8%96%E5%85%A7%E5%AE%B92_Page%E6%97%85%E9%83%A8%E7%B0%A1%E4%BB%8B
