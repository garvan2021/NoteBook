# Web Basic

- OSI model
![OSI model](../pics/OSI-vs.-TCPIP-models.jpg)

- WebSocket vs HTTP  
https://ably.com/topic/websockets-vs-http#:~:text=Unlike%20HTTP%20with%20its%20request,client%20to%20issue%20a%20request.

- When Ping(ICMP) is blocked, How to test website latency
  - using curl:
    ```shell
    curl -w "time_namelookup: %{time_namelookup}\ntime_connect: %{time_connect}\ntime_starttransfer: %{time_starttransfer}\ntime_total: %{time_total}\n" -o /dev/null -s https://{domain}
    ```
  - using hping3
    ```shell
    sudo hping3 -S -p 443 {domain}
    ```
  > Replace {domain} to the target webiste's domain
