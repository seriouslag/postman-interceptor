# Postman Interceptor Setup

Postman Interceptor is a Chrome extension that syncs up cookies from selected domains with Postman. This can be useful to always have your latest login auth cookie, so Postman can fetch your auth tokens for requests.

## Prerequisites
- Ensure that Postman is up to date (version ~10.12.10).

## Installation
1. Download and install the [Postman Interceptor extension](https://chrome.google.com/webstore/detail/postman-interceptor/aicmkgpgakddgnaphhhpliifpcfhicfo?hl=en) from the Chrome Web Store.
2. Ensure that Interceptor is marked as connected and syncing.
	![Click cookies button](./images/cookies_button.png)
	- Open the Cookies menu and navigate to the Sync tab.
  - Install the interceptor bridge if not installed
	- Any time you log in to a Tradeshift domain, your cookies will be synced with Postman.
	![Sync cookies](./images/sync_cookies.png)
3. Whitelist selected domains in the extension and turn on cookie capture:
	-![Set up extension.](./images/set_up_extension.png)
	- Open the extension settings and select the "Cookies" tab.
	- Add in the Tradeshift domains to the domains multi-select.
	- Turn on cookie capture.
4. Select a environment:
	![Select environment](./images/collection_dropdown.png)
	- Select the collection dropdown and choose your desired environment.
5. Pre-request script:
	- A pre-request script was added to the 'Tradeshift' collection.
	- This script will check for a valid environment and auth cookie, then will fetch an auth bearer token.
	- The script only runs once a minute unless your cookie changes.
	![Collections](./images/collections.png)
	![Pre-request scripts](./images/prerequest_script.png)

## Troubleshooting
If facing any issues, please check the console for any errors. There should be plenty of logs to help you debug.

## Note on Environments
The environments are global, so we may end up sharing tokens between users. We may need to look into how we can access variables local to our machine, but in the meantime, this setup should work.
