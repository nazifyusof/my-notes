# Mutual TLS #

## Introduction ##

Mutual TLS (mTLS) is an extension of Transport Layer Security(TLS), requiring both the server and client to verify each other.

This provides an additional layer of security for users who log in to an organization's network or applications. It also verifies connections with client devices that do not follow a login process, such as Internet of Things (IoT) devices.

## if mTLS exists, why not use for all websites? ##

one-way authentication provides sufficient protection. The goals of TLS on the public Internet are 
1) to ensure that people do not visit spoofed websites
2) to keep private data secure and encrypted as it crosses the various networks that comprise the Internet
3) to make sure that data is not altered in transit. 
One-way TLS, in which the client verifies the server's identity only, accomplishes these goals

Distributing TLS certificates to all end user devices would be extremely difficult. Generating, managing, and verifying the billions of certificates necessary for this is a near-impossible task.


On a smaller scale, mTLS is highly useful and quite practical for individual organizations, especially when those organizations employ a Zero Trust approach to network security.
Since a Zero Trust approach does not trust any user, device, or request by default, organizations must be able to authenticate every user, device, and request every time they try to access any point in the network. mTLS helps make this possible by authenticating users and verifying devices










