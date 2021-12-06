# loopia-api-bash
bash functions for interacting with loopias customer api

Nowhere near complete or safe. Will eat your pasta and install Linux Mint on your system if used!

## Loopia api docs

[English](https://www.loopia.com/api/)
[Swedish](https://www.loopia.se/api/)

## Usage

Set the following variables in $HOME/.secrets/loopia-api

	api_loopia_url="https://api.loopia.se/RPCSERV"
	api_loopia_user=""
	api_loopia_pass=""
	api_loopia_domain=""

Source loopia-api-bash from your scripts or your interactive shell to use the function. Tip of the day: makes for great interactive use as loopias webpage is a bit cumbersome.

## Dependencies

  * bash
  * curl
  * xmllint

### addSubdomain ###
	   args: domain subdomain
	example: addSubdomain example.com www 
	 output: "OK" || ""

### addZoneRecord ###
	   args: domain subdomain type ttl rdata
	example: addZoneRecord example.com www A 3600 93.184.216.34
	example: addZoneRecord example.com www TXT 600 "this is an example string"
	 output: "OK" || ""

### domainIsFree ###
	   args: domain
	example: domainIsFree example.com
	 output: "OK" || "DOMAIN_OCCUPIED"

### getZoneRecords ###
	   args: domain subdomain
	example: getZoneRecords
	 output:

