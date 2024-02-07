# DNS Management Lab Exercise

## A-Record Exercise

1. Connect/log into DC-1 as your domain admin account (mydomain.com\jane_admin).
   
2. Connect/log into Client-1 as an admin (mydomain\jane_admin).
   
3. From Client-1, try to ping “mainframe” and notice that it fails.
   
4. Nslookup “mainframe” and notice that it fails (no DNS record).
   
5. Create a DNS A-record on DC-1 for “mainframe” and have it point to DC-1’s Private IP address.
   
6. Go back to Client-1 and try to ping it. Observe that it works.

## Local DNS Cache Exercise

1. Go back to DC-1 and change mainframe’s record address to 8.8.8.8.
   
2. Go back to Client-1 and ping “mainframe” again. Observe that it still pings the old address.
   
3. Observe the local DNS cache (`ipconfig /displaydns`).
   
4. Flush the DNS cache (`ipconfig /flushdns`). Observe that the cache is empty.
   
5. Attempt to ping “mainframe” again. Observe that the address of the new record is showing up.

## CNAME Record Exercise

1. Go back to DC-1 and create a CNAME record that points the host “search” to “www.google.com”.
   
2. Go back to Client-1 and attempt to ping “search”. Observe the results of the CNAME record.
   
3. On Client-1, nslookup “search”. Observe the results of the CNAME record.

## Finish

Congratulations! You have successfully completed the DNS Management Lab Exercise.
