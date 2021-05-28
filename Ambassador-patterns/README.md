<img width="582" alt="Screen Shot 2021-05-28 at 0 40 45" src="https://user-images.githubusercontent.com/12546802/119856046-61da1000-bf4d-11eb-8f57-91efd6407377.png">

An Ambassador container is a sidecar container that is in charge of proxying connections from the application container to other services.
So, why do we need to proxy the application connection requests? Because we need to follow `the separation of concerns principle`. Each container should do it’s task and do it well. If there are other tasks that requires the application’s function in order to work correctly, we may hand those tasks to the sidecar container. As you can see on the above diagram,  the Ambassador container hides the complexity and provides the uniform interface to access these external services.

The value of the ambassador pattern is twofold. First, as with the other single-node patterns, there is inherent value in building modular, resuable containers. The separation of
concerns makes the containers easier to build and maintain. Likewise, the ambassador container can be reused with a number of different application containers. 
This reuse speeds up application development because the container’s code can be reused in a number of places. Additionally the implementation is both more consis‐ tent and of a higher quality because it is built once and used in many different con‐ texts.
