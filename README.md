# Living Legend
made with the ArcGIS Maps SDK for JavaScript, Node.js and ESP32.

---

Send the map legend to a RGB LED strip like [here](https://www.instagram.com/reel/CpglP7nA4MB)!


## This repo
Run a small Node.js application on localhost that receives data from the map, transforms it into Artnet and sends it over to the ESP32.

Enter IP of your ESP in the ```package.json``` start script or better, create your own script!

```
"start": "node server.js -a <ESP_IP> -p 9000 -v"
```

## Other repos needed to make sense of this

### esp32_artnet
Use this [ESP32 firmware](https://github.com/esride-nik/esp32_artnet) to receive data from ``artnet-http`` and put it on your LED strip via FastLED.


### jssdk-artnet-webclient
This is the webmap with [logic for legend2LEDs](https://github.com/esride-nik/jssdk-artnet-webclient).




---


```

artnet-http bridge

  Bridges HTTP POST requests to ArtNet UDP 

Options

  -a, --artnet_host string   IP address of the ArtNet server.            
  --artnet_port number       ArtNet UDP port (6454 is standard.)         
  -p, --listen_port number   HTTP port to listen on.                     
  -v, --verbose              Display transmitted packets on the console. 

Examples

  Start the HTTP server on the default port, sending ArtNet requests to         
  localhost                                                                     
                                                                                
  $ node server.js -h 127.0.0.1                                                 
                                                                                
  Start the HTTP server on port 9000, sending ArtNet requests to a remote host, 
  with verbose output                                                           
                                                                                
  $ node server.js -v -h 10.0.1.17 -p 9000                                      

HTTP interface

  The server will listen on / for POST requests. Posting a JSON body containing 
  an array of numbers between 0 and 255 will write those values to ArtNet       
  universe 0, starting with channel 1. For example:                             
                                                                                
  $ curl -X POST 127.0.0.1:8000 -H "Content-Type: application/json" -d "[255,   
  255, 255]"                                                                    
                                                                                
  You can optionally provide a universe and starting channel number in the HTTP 
  route. For example, to set the first three channels of universe 2 to 255:            
                                                                                
  $ curl -X POST 127.0.0.1:8000/2 -H "Content-Type: application/json" -d "[255, 
  255, 255]"                                                                    
                                                                                
  To set channels 12, 13, and 14 of universe 4 to 0:                            
                                                                                
  $ curl -X POST 127.0.0.1:8000/4/12 -H "Content-Type: application/json" -d     
  "[0, 0, 0]"                  

```