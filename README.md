# Lab 3
Look at the captured trace (Note: I was having issues with traceroute on my Mac with security software so I used the suggested ip-ethereal-trace-1 trace file.)
![image](https://user-images.githubusercontent.com/25465133/172072998-75834a21-26a2-4b14-b18f-f8beae81bc56.png)
1. The IP address of the computer in the given trace route file is shown in the source column for the first ICMP Request and is 192.168.1.102
2. Listed under “Protocol:” In the IPv4 tab is “ICMP (1)”
3. “Header length: 20 bytes (5)”, “Total Length: 84”
    - Header: 20 bytes, Payload: 84 - 20 = 64 bytes
4. This datagram has not been fragmented, this is shown under the “Flags 0x00” tab with: “.0.. …. = Don’t fragment: Not set”
![image](https://user-images.githubusercontent.com/25465133/172073023-ca26acca-2005-4f3a-9699-bbd00965725b.png)
5. “Identification:”, “Time to Live:”, and “Header Checksum:” will always change from one datagram to another.
6. “Version”, “Header Length”, “Differentiated Services Field”, “Protocol”, “Source Address”, and “Destination Address” stay constant and must stay constant. While “Identification:”, “Time to Live:”, and “Header Checksum:” change. The ones that stay constant have to do with the protocols of the connection while will not change within communication. The others have to do with each individual datagram and therefore will change each time.
7. The value in the identification field of the IP datagram increased with each datagram.
8. “Identification: 0x9d7c (40316)”, “255”
9. TTL stays the same remain unchanged for all of the ICMP TTL-exceeded replies sent to the computer by the nearest router. This is because TTL stays the same for each individual hop, all to the first hop are the same, all to the second are the same, and so on.
![image](https://user-images.githubusercontent.com/25465133/172073034-d0db67e1-4b7b-44ef-bdf6-4471ac04df46.png)
![image](https://user-images.githubusercontent.com/25465133/172073041-25e5b691-4099-4438-b46e-0a57b4e5d18b.png)
10. In the above datagram, we can see “[2 IPv4 Fragments (2008 bytes): #92(1480), #93(528)]” showing that the message has been fragmented into more than one datagram.
11. Wireshark appears to showing the fragmented packets together, however we can determine the first fragment is #92. Looking at header info for said fragment, we would be able to tell the difference between the two by looking at the fragment offset. If said offset is zero, it is the first fragment.
12. The second fragment is also shown in the image above. We can tell this is not the first fragment of the datagram because we can see an offset of 1480
13. “Total length”, “More fragments”, and “Fragment Offset” will change between the fragments.
![image](https://user-images.githubusercontent.com/25465133/172073054-32040396-049a-433d-80df-aa306d083636.png)
14. Three fragments were created from the original datagram.
15. Fragment offset and checksum is different for each, total length is 1480 for the first two, but 548 for the third. Also the first two have more fragments set two 1, whereas the third is 0.
