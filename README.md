# Keeping-Cloud-APIs-Warm

## Overview
This repo shows a hacky way of handling the cold start issue with Google Cloud services, using a simple GitHub Action automation script. 

The issue I had, was that I wanted my APIs to have fast initial response times when I know I want to use them; however, I didn't want their servers to be running 24/7, such that they are always racking up costs. This is especially important for services which have GPU backends, as they are very expensive.

So my solution was to make a script which pings the servers for a specified period of time, at a specified interval. 

![Alt text](workflow.gif)

## Why is this useful? 
Lets imagine you know at what times you want your APIs to be warm. This could be useful when you need to demo a project to someone, but you dont want your servers running 24/7 as your APIs are used at high volume but in sparse intervals. 

You can manually run the warm up script for the specified period of time, such that they will be warmed up when you need them to be, and then scale back down to 0 when the script is finished. 

## How it works
- Generate a token for every API
- Using bash script, iterate using a while loop, which starts at the current time, and ends at the current time + the specified time parameter. 
    - Ping each API using the generated token and curl




