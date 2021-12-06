# loopia-api-bash
bash function library for interacting with loopias customer api

Nowhere near complete or safe. Will eat your pasta and install Linux Mint on your system if used!

Follows loopia docs naming conventions and such as close as possible. Reseller functionality will not be implemented (by me). XML parsing sucks and XPath belongs in hell!

WARNING! NO sanity checks of params WHAT SO EVER! Adding a domain will likely cost real money. There might be other functionality that will cost you that I am not aware of.

## Loopia api docs

[English](https://www.loopia.com/api/)
[Swedish](https://www.loopia.se/api/)

## Usage

Set the following variables in $HOME/.secrets/loopia-api

	api_loopia_url="https://api.loopia.se/RPCSERV"
	api_loopia_user=""
	api_loopia_pass=""
	api_loopia_domain=""

Source loopia-api-bash from your scripts or your interactive shell to use the functions. Tip of the day: makes for great interactive use as loopias webpage is a bit cumbersome.

TODO: add -h|--help flags for interactive use. Probably argument checks too. Maybe some kind of --dryrun too.

TODO: Actually implement core funtionality.

## Dependencies

  * bash
  * curl
  * xmllint

## Actual docs

### addSubdomain ###
Tested. Works.

	   args: domain subdomain
	example: addSubdomain example.com www 
	 output: "OK" || ""

### addZoneRecord ###
Unsafe. Works but gets "UNKNOWN_ERROR" on non-ascii.

	   args: domain subdomain type ttl rdata
	example: addZoneRecord example.com www A 3600 93.184.216.34
	example: addZoneRecord example.com www TXT 600 "this is an example string"
	 output: "OK" || "UNKNOWN_ERROR"

### domainIsFree ###
Safe to use.

	   args: domain
	example: domainIsFree example.com
	 output: "OK" || "DOMAIN_OCCUPIED"

### getZoneRecords ###
Not done determining how output should be formated. CSV and SSV is out the door because of the nature on TXT records containing most anything.

	   args: domain subdomain
	example: getZoneRecords
	 output:

