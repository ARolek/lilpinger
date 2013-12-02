# lilpinger


lilpinger is a small site pinging tool I wrote to notify me via SMS and email if any of the properties I manage are running slow or having connection problems. Pinging each URL happens in a separate goroutine allowing for lags and errors for each URL to be independent of each other.

## Features
- Pings a list of stites once per ping interval in seperate go routines
- SMS and email notifications for:
	- connection errors
	- response times over lag threshold
	
## Configuration
All configuration is handled inside lilpinger.toml. The following params can be set:

- **PingInterval**: How often to ping each url, in seconds
- **LagThreshold**: If response time is slower than this, send alert (in seconds)    
- **URLsFile**: Path to a text file of URLs to ping. Each URL needs to be on a new line. File path can be a relative our absolute reference.  
- **Twilio**: Credentials for SMS notifications via Twilio
- **SMTP**: Credentials for email account to send notifications from
- **Notify**: Mobile phones and emails to notify on ping errors or slow responses.

## Runing lilpinger

### From Go source

```
go run lilpinger
```

You will see output for each url in your URLsFile. 

### Compiled version as a foreground process
This will ouput ping data to the console

```
./lilpinger
```

### Compiled version as a background process
This will create a lilpinger.log file with lilpinger's output

```
./lilpinger > lilpinger.log &
```