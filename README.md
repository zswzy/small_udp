# small_udp

A simple header-only library for UDP communication in Windows.

## Installation
Download ```server.h``` in your folder and include it.

## Example
```cpp
#include <stdio.h>
#include <server.h>
int main()
{
    // Create my udp
    UdpCom udp_test = UdpCom();
    
    // Open udp with local IP & port and remote IP & port.
    udp_test.Open("127.0.0.1", 15000, "127.0.0.1", 20000);

    // Set and send message
    char msg[4096];
    strcpy_s(msg, sizeof msg, "This is a message from cpp.");
    udp_test.Send(msg);

    // Receive message
    udp_test.Receive();
    char* msg_receive = udp_test.GetContent();
    printf("Receive message: %s", msg_receive);

    // Send again a new message
    strcpy_s(msg, sizeof msg, "This is what I receive: ");
    strcat_s(msg, sizeof msg, msg_receive);
    udp_test.Send(msg);

    return 0;
}
```
