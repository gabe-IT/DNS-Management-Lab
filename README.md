# DNS Management Lab Exercise

## A-Record Exercise

1. **Connect/log into DC-1 as your domain admin account (mydomain.com\jane_admin)**:
   - Open Remote Desktop Connection or use Azure Portal to connect to DC-1.
     ![Screenshot_1](https://github.com/gabe-IT/DNS-Management-Lab/assets/148400020/cf882b93-7739-4938-b5d5-813fcd372dbb)

   - Log in using the credentials for the domain admin account.

2. **Connect/log into Client-1 as an admin (mydomain\jane_admin)**:
   - Open Remote Desktop Connection or use Azure Portal to connect to Client-1.
   - Log in using the credentials for the admin account (mydomain\a-gabe).

3. **Attempt to Ping "mainframe" from Client-1**:
   - Open Command Prompt on Client-1.
   - Type `ping mainframe` and notice that it fails to resolve.

4. **Nslookup for "mainframe"**:
   - In the same Command Prompt on Client-1, type `nslookup mainframe`.
   - Observe that it fails to find the DNS record for "mainframe".

5. **Create a DNS A-record for "mainframe" on DC-1**:
   - Return to DC-1.
   - Open DNS Manager.
     ![Screenshot_2](https://github.com/gabe-IT/DNS-Management-Lab/assets/148400020/0333a951-b01f-419c-a02b-5d998fe49508)

   - Navigate to the forward lookup zone for your domain.
   - Create a new A-record for "mainframe" pointing to DC-1’s Private IP address.
     ![Screenshot_3](https://github.com/gabe-IT/DNS-Management-Lab/assets/148400020/16fef11b-0c69-48a2-ac77-1c5ca29ef438)
![Screenshot_4](https://github.com/gabe-IT/DNS-Management-Lab/assets/148400020/243e6479-ecfb-4c30-832a-51e81880413a)


6. **Verify Ping Connectivity from Client-1**:
   - Go back to Client-1.
   - Ping "mainframe" again (`ping mainframe`) and observe that it resolves successfully.
![Screenshot_6](https://github.com/gabe-IT/DNS-Management-Lab/assets/148400020/ffdbaa5b-18aa-491e-ab11-5bb013afb216)

## Local DNS Cache Exercise

1. **Change mainframe's Record Address on DC-1**:
   - Return to DC-1.
   - Edit the A-record for "mainframe" in DNS Manager to point to 8.8.8.8.
![Screenshot_8](https://github.com/gabe-IT/DNS-Management-Lab/assets/148400020/f340681b-be14-4f4d-a0f4-e90b3b12766b)

2. **Ping "mainframe" from Client-1 Again**:
   - Go back to Client-1.
   - Ping "mainframe" (`ping mainframe`) and notice that it still resolves to the old address.
![Screenshot_9](https://github.com/gabe-IT/DNS-Management-Lab/assets/148400020/6023064c-747d-411b-85cf-a650afe617f0)

3. **Observe the Local DNS Cache on Client-1**:
   - Open Command Prompt on Client-1.
   - Type `ipconfig /displaydns` to view the local DNS cache.

4. **Flush the Local DNS Cache**:
   - In the same Command Prompt, type `ipconfig /flushdns`.
   - Observe the message confirming the cache has been flushed.

5. **Attempt to Ping "mainframe" Again**:
   - Ping "mainframe" (`ping mainframe`) and notice that it now resolves to the new address.
![Screenshot_10](https://github.com/gabe-IT/DNS-Management-Lab/assets/148400020/2f1a6d49-bb73-4a60-a5f1-5eec437813f7)

## CNAME Record Exercise

1. **Create a CNAME Record on DC-1**:
   - Return to DC-1.
   - Open DNS Manager.
   - Navigate to the forward lookup zone for your domain.
   - Create a new CNAME record for "search" pointing to "www.google.com".
![Screenshot_12](https://github.com/gabe-IT/DNS-Management-Lab/assets/148400020/2a1da001-6244-4010-81a7-edb8e52d3eb2)

2. **Attempt to Ping "search" from Client-1**:
   - Go back to Client-1.
   - Ping "search" (`ping search`) and observe the results showing the resolved IP address of "www.google.com".
![Screenshot_13](https://github.com/gabe-IT/DNS-Management-Lab/assets/148400020/7f8ba947-2ac9-4b85-bd01-b75fc2629990)

3. **Nslookup "search" on Client-1**:
   - In Command Prompt on Client-1, type `nslookup search`.
   - Observe the results showing the canonical name (CNAME) record for "search" pointing to "www.google.com".
![Screenshot_14](https://github.com/gabe-IT/DNS-Management-Lab/assets/148400020/12e9c744-07bb-4eac-bfdb-fc8b33878f7b)
![Screenshot_15](https://github.com/gabe-IT/DNS-Management-Lab/assets/148400020/38337def-5639-4437-907e-4a73cdfc17ea)
![Screenshot_16](https://github.com/gabe-IT/DNS-Management-Lab/assets/148400020/2ed29556-2860-4a95-9308-b162185386a9)

## Finish

Congratulations! You have successfully completed the DNS Management Lab Exercise.
