## Sync charge

By default it fetches invoices with `processed` value **less** then  `\App\Services\Invoice::TYPE_PROCESSED (4)` i.e  `\App\Services\Invoice::TYPE_NEW (0)` and `\App\Services\Invoice::TYPE_FILED (2)`.

### Invoice date limiting
By default we only try to process invoices NOT OLDER then 30 days from upload.

If customer did not pay for a certain amount of time it will start Telavox' dunning flow process where they send notifications to customers via email and SMS for approx with [[Resubscribe]] link. 

After approx 20 days they block customers mobile subscription if they are still hasn't paid. At this point we would not need to try to charge customer anymore.

After this date if customer still wants to pay their pervious invoices they can do it via [[Resubscribe]] link and we will [[Resubscribe#Invoice reset|reset their invoice status]]

```
Usage:
sync:charge [options] [--] <country>

Arguments:
  country

Options:

--subscription[=SUBSCRIPTION] Only charges specific subscription
--invoice-type[=TYPE]         Sync only specific invoice type (f.ex. only new invoices and skip failed)
--all-the-time.               Do not limit [[#Invoice date limiting]]
--dry-run                     Test run 
--validate-mandate            Checks for mandate's validity via payment APIs, can be cancelled with combination with {--cancel-invalid}

--find-mandate                 Works with combination with {--subscription} - displays info about mandate for gives subscription id
--cancel-invalid Cancel invalid payment mandates. See {--find-mandate}
--skip-failed                  Do not process `\App\Services\Invoice::TYPE_FAILED` invoices
```

## Sync download

Telavox / eRate has FTP server (logins are different per country) where they upload their invoice files in CSV format. `sync:download` gets this data, processes CSV files and inserts then into database to `invoices` table. 

Uses [league/csv](https://csv.thephpleague.com/) for reading CSV files.

```
Usage:
sync:download [options] [--] <country>

Arguments:
  country

Options:
	  --resync   Tries to reimport already processed files
      --local    Reads files for local filesystem instead of FTP 
      --backup   Saves files locally
      --list     Only lists files and folders
```

## Sync upload

Reads processed invoices (`processed = 2` or `\\App\\Services\\Invoice::TYPE_PROCESSED`) from `invoices` table makes CSV files with `out-{Y.m.d.H}.csv` format and upload them to FTP server provided by Telavox.


> [!warning] Changes status of invoices in the database
> Chnges status of invoices from `\App\Services\Invoice::TYPE_PROCESSED` to `\App\Services\Invoice::TYPE_UPLOADED`


```
Usage:
sync:upload [options] [--] <country>

Arguments:
  country

Options:
      --local    Writes files to local filesystem instead of FTP 
      --dry-run  Outputs data to CLI for inspection, doesn't change status or uploads any files
```
