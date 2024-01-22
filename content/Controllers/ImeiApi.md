### \\App\\Http\\Controllers\\ImeiApi

ImeiApi is an API controller which returns information about specific IMEI number. API keys are managed by laravel/sanctum 

```
REQUEST GET /api/imei/{imei}

RESPONSE
{
	"imei_status"         : <int> 
	"plan_status"         : <int> 
	"subscription_status" : <int>  
}

```

- Watch type (`imei_status`): 
	- IMEI not found  (-1)
	- SIM Pre-installed  (1) 
	- SIM in the box (SIM Free)  (2) 
	- Partner watch (3) Uses [[Imei#^surface-db]]
- Subscription Status (`subscription_status`):
	- Activated - (0)
	- not activated - it has never been activated (-1)
	- not activated - it has been activated before (-2)
- Last/Latest Plan (`plan_status`):  
	- basic  (1)
	- premium  (2) 
	- service fee (3) 
	- other plan  (9)