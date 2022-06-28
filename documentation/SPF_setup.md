# Set up DNS for your application

## Main domain
The canonical domain for you application, ie www.natcheurope.com or shop.natcheurope.com

Use a single C-name record to point to the hostname you received from Natch, ie lb00.natchcloud.com. Make sure you don't have a duplicate entry as an A-record.

![This is an image](/cname_combell.png)


A TTL (time to live) value of 300 seconds is recommended.



## Naked domain

A naked domain is one without www, ie natcheurope.com. Depending on the option your registrar offers, you can use forwarding or an external service.

*Does your registrar support web forwarding?*
Configure the web forward to redirect to your canonical domain (ie. www.natcheurope.com). Make sure the redirect is set to a HTTPS address and Cloaking is not enabled.

![This is an image](/webforwarding_mycombell.png)

*Does your registrar not support web forwarding?*
Consider moving to a registrar that supports web forwarding, like [Combell](www.combell.com).

Otherwise, point your naked domain to 174.129.25.170 using an A-record. This is a free server by [wwwizer](http://wwwizer.com/naked-domain-redirect) that forwards the naked domain to the www domain.



