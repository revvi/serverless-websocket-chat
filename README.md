# General

# Architecture

- API Gateway websockets
- Lambda
- DynamoDB
- DynamoDB Streams (just to demo some durability)

# Chat Protocol

### Connect

`npm i -g wscat` - to install WebSocket cat

`wscat -c wss://ws.kiostix.com/{ApiStage}` 

example:
`wscat -c wss://ws.kiostix.com/prod`

### Channel Subscriptions

Subscribe to channel:

`{"action": "subscribeChannel", "channelId": "Secret", "name": "Adam"}`

Unsubscribe from channel:

`{"action": "unsubscribeChannel", "channelId": "Secret"}`

### Messages

`{"action": "sendMessage", "name": "Adam", "channelId": "General", "content": "hello world!"}`

### Get channel history

(coming soon)

# Deployment

Install serverless

`npm install -g serverless`

Set credentials in `~/.aws/credentials`, then create `kiostixProfile` with current aws_access_key_id and aws_secret_access_key. 

Reference:
https://www.serverless.com/framework/docs/providers/aws/guide/credentials/

Example:

```
[kiostixProfile]
aws_access_key_id=xxxxxxxxxx
aws_secret_access_key=xxxxxxxxxx
```

Deploy

`serverless deploy`

# Test

## Install Artillery

Install Artillery
`npm i -g artillery`

Run Test
`artillery run test-websocket.yml`