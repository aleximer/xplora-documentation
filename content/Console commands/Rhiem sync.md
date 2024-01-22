Sync orders from Rhiem warehouse, if order status  is shipped and `Positions->Position->Serials->Serial->SerialNumber` is set  and it's a valid IMEI address: watch with this IMEI number exists in database, and is not taken and does not have subscription ID we try to activate watch' mobile subscription.

Command uses [Rhiem Soap](obsidian://open?vault=xplora&file=Xplora%2FShipping%20and%203PL%20integrations#Rhiem integration Germany and France) service

```bash
Usage:
rhiem:sync [options] [--] <country>

Arguments:
  country

Options:
      --to[=TO]                Amount of days to sync
      --from-date[=FROM-DATE]  Date to sync from in Y-m-d format
      --reference[=REFERENCE]  Only check specific Shopify order
      --notify                 Notify CS slack channel on any errors
```

