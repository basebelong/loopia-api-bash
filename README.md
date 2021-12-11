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
[loopia docs](https://www.loopia.com/api/getcreditsamount/)
Tested. Works.

	   args: domain subdomain
	example: addSubdomain example.com www 
	 output: "OK" || ""

### addZoneRecord ###
[loopia docs](https://www.loopia.com/api/addzonerecord)
Unsafe. Works but gets "UNKNOWN_ERROR" on non-ascii.

	   args: domain subdomain type ttl rdata
	example: addZoneRecord example.com www A 3600 93.184.216.34
	example: addZoneRecord example.com www TXT 600 "this is an example string"
	 output: "OK" || "UNKNOWN_ERROR"

### domainIsFree ###
[loopia docs](https://www.loopia.com/api/domainisfree)
Safe to use.

	   args: domain
	example: domainIsFree example.com
	 output: "OK" || "DOMAIN_OCCUPIED"

### getZoneRecords ###
[loopia docs](https://www.loopia.com/api/getzonerecords)
Not done determining how output should be formated. CSV and SSV is out the door because of the nature on TXT records containing most anything. First word is a key and til end of line is value.

	   args: domain subdomain
	example: getZoneRecords
	 output:

### getCreditsAmount ###
[loopia docs](https://www.loopia.com/api/getcreditsamount/)
0 for amount without VAT, 1 for amount including VAT (default if not given argument)
	   args: [0|1]
	example: getZoneRecords 0
	 output: double

### getDomain ###
[loopia docs](https://www.loopia.com/api/getdomain/)
Safe to use.

	   args: domain
	example: getDomain example.com
	 output: 

### getDomains ###
[loopia docs](https://www.loopia.com/api/getdomains/)
Safe to use.

	   args:
	example: getDomain
	 output: 

### getInvoice ###
[loopia docs](https://www.loopia.com/api/getinvoice/)
Safe to use.
Get invoice number with getUnpaidInvoices.

	   args: reference_no
	example: getInvoice 123123123 0
	 output:

### getUnpaidInvoices ###
[loopia docs](https://www.loopia.com/api/getunpaidinvoices/)
Unsafe.
Have no idea how it would handle severla unpaid invoives. Works fine when there is only one single.

	   args:
	example: getUnpaidInvoices
	 output:

