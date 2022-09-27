# workshop-api-styles-fundamentals

1. OSI

- https://www.infoq.com/presentations/history-api/
- https://www.youtube.com/watch?v=aAb7hSCtvGw
- https://www.cloudflare.com/learning/ddos/glossary/open-systems-interconnection-model-osi/
- https://www.geeksforgeeks.org/layers-of-osi-model/
- https://infosys.beckhoff.com/english.php?content=../content/1033/tf6310_tc3_tcpip/84246923.html&id=
- https://www.imperva.com/learn/application-security/osi-model/
- https://cloud.google.com/blog/topics/developers-practitioners/differences-between-synchronous-web-apis-and-asynchronous-stateful-apis
- https://en.wikipedia.org/wiki/Duplex_(telecommunications)#FULL-DUPLEX
- https://cloud.google.com/blog/topics/developers-practitioners/differences-between-synchronous-web-apis-and-asynchronous-stateful-apis
- https://www.soapui.org/learn/api/soap-vs-rest-api/
- https://en.wikipedia.org/wiki/OpenAPI_Specification
- https://developers.google.com/protocol-buffers
- https://en.wikipedia.org/wiki/Apache_Thrift
- https://en.wikipedia.org/wiki/Apache_Avro
- https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol
- https://www.digitalocean.com/community/tutorials/http-1-1-vs-http-2-what-s-the-difference
- https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/Evolution_of_HTTP
- https://css-tricks.com/http2-real-world-performance-test-analysis/
- https://medium.com/walmartglobaltech/introduction-to-http-2-d3e3b4f4d662
- https://stackoverflow.com/questions/58498116/why-is-it-said-that-http2-is-a-binary-protocol
- https://developer.mozilla.org/en-US/docs/Web/HTTP
- https://freecontent.manning.com/animation-http-1-1-vs-http-2-vs-http-2-with-push/
- https://http3-explained.haxx.se/en/h3/h3-h2
- https://avinetworks.com/glossary/ssl-termination/
- https://www.ibm.com/docs/en/aix/7.2?topic=protocols-transmission-control-protocol
- https://ntrs.nasa.gov/api/citations/20080030196/downloads/20080030196.pdf
- https://www.json.org/json-en.html

Custom RPC protocols with a binary encoding format can achieve better performance than something generic like JSON over REST. However, **a RESTful API has other significant advantages:** it is good for experimentation and debugging (you can simply make requests to it using a web browser or the command-line tool curl, without any code generation or software installation), it is supported by all mainstream programming languages and platforms, and there is a vast ecosystem of tools available (servers, caches, load balancers, proxies, firewalls, monitoring, debugging tools, testing tools, etc.).

For these reasons, REST seems to be the predominant style for public APIs. The main focus of RPC frameworks is on requests between services owned by the same organization, typically within the same datacenter.
