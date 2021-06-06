The circuit breaker is a proxy that controls flow to an endpoint. If the endpoint fails or is too slow (based on your configuration), the proxy will open the circuit to the container.
In that case, traffic is routed to other containers because of load balancing. The circuit remains open for a preconfigured sleep window (let's say two minutes) after which the circuit is considered "half-open". 
The next request attempted will determine if the circuit moves to "closed" (where everything is working again), or it it reverts to "open" and the sleep window starts again.

<img width="817" alt="Screen Shot 2021-06-06 at 23 56 28" src="https://user-images.githubusercontent.com/12546802/120929149-de75a700-c722-11eb-9b2c-8e35004371c5.png">

Having circuit breaker is a way to protect our microservices in case of certain conditions occur, such as preventing that an unexpected number of requests overflow and
affect the microservices in the service mesh. 

## Demo circuit breaking with envoy proxy
This demo is borrowed from this awesome tutorial: https://blog.christianposta.com/microservices/01-microservices-patterns-with-envoy-proxy-part-i-circuit-breaking/ <br>

<img width="816" alt="Screen Shot 2021-06-07 at 0 03 38" src="https://user-images.githubusercontent.com/12546802/120929398-de29db80-c723-11eb-9632-412e96f915b8.png">

In this demo, Envoy is deployed as a sidecar alongside the service (the http client in this case). When the http-client makes outbound calls (to the "upstream" httpbin.org service),
all of the calls go through the Envoy Proxy sidecar.
