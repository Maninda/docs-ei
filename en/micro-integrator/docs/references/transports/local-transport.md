# Local Transport

Apache Axis2's local transport implementation is used to make fast,
in-VM (Virtual Machine) service calls and transfer data within [proxy
services](https://docs.wso2.com/display/EI650/Working+with+Proxy+Services)
. The transport does not have a receiver implementation. The following
class implements the sender API:

-   `          org.apache.axis2.transport.local.NonBlockingLocalTransportSender         `

!!! Info
    -   WS-Security cannot be used with the local transport. Since the local is mainly used to make calls within the same VM, WS-Security is generally not required in scenarios where it is used.
    -   If you want to make calls across tenants, you should use a non local transport even if they run from the same VM.
    -   If you need to use local transport with callout mediator, you do not need to perform configuration mentioned in this section as callout mediator requires blocking local transport which is configured by default in WSO2 Enterprise Integrator distribution.

To use this transport, configure an endpoint with the `         local://        ` prefix. For example, to make an in-VM call to the HelloService, use `         local://services/HelloService        ` . Note that the local
transport cannot be used to send REST API calls, which require the HTTP/S transports.

## Configuring the Local Transport

By default, WSO2 EI provides CarbonLocalTransportSender and
CarbonLocalTransportReceiver, which are used for internal communication
among Carbon components and are not suitable for WSO2 EI service
invocation. To enable the local transport for service invocation, follow
these steps.

Update the following configuration to enable the endpoint in the ei.toml file:

```toml
```

Update the following cofnigurations in the ei.toml file:

```toml
[transport.local]
listener.enabled=false
sender.enabled=false
```

For more information about transports, see Carrying Messages .

## Example

There are three proxy services in WSO2 EI named
`         LocalTransportProxy        ` , `         SecondProxy        `
and `         StockQuoteProxy        ` . The invocation of services take
place in the following order:

1.  1.  The stockquote client invokes
        `            LocalTransportProxy           ` .
    2.  The message received is forwarded to
        `            SecondProxy           ` .
    3.  The message is forwarded to
        `            StockQuoteProxy           ` .
    4.  `            StockQuoteProxy           ` invokes the backend
        service.
    5.  `            StockQuoteProxy           ` receives a response.
    6.  The response is returned by
        `            StockQuoteProxy           ` to
        `            SecondProxy           ` .
    7.  The response is returned by `            SecondProxy           `
        to `            LocalTransportProxy           ` .
    8.  The response is returned by
        `            LocalTransportProxy           ` to the client.

When local transport is not used, the messages sent by one proxy service
to another (i.e. flows b, c, f and g) goes through the network as
shown in the following diagram.

![](attachments/119130361/119130363.png)

Local transport can be used as shown below to prevent message flows
between proxy services from going through the network. When local
transport calls are in JVM calls, the time taken for communication
between proxy services will be reduced since no network overhead will be
introduced.

![](attachments/119130361/119130362.png)
