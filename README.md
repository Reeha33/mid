T1:
For VM:

sudo apt update
sudo apt upgrade –y

lsblk
sudo mkfs -t ext4 /dev/sdc

sudo mkdir /data
sudo mount /dev/sdc /data

sudo blkid /dev/sdc
sudo nano /etc/fstab
line added:
UUID=<your-copied-uuid> /data ext4 defaults 0 0

Verify
sudo umount /data
sudo mount -a
df -h
for install webserver:
sudo apt install apache2 –y
for this firdt allow HTTP(80)port go into network setting and add inbound 





T2:
Create storage account then go to resource and then select blob after this add container .and in container then upload file .
For blob go to storage account “configuration and enable “Allow Blob access”
Then also change container access

For file first create VM that in window and select inbound port RDP(3389)
Phase 2: Open Port 445 (CRITICAL)
Azure blocks SMB traffic (Port 445) and also RDP(3389)must be added otherwise it never work by default. If you don't do this, your file share will fail to mount with a "Network Error."
1.	Navigate to your new VM in the Portal.
2.	On the left sidebar, click Networking.
3.	Click Add inbound port rule.
4.	Destination port ranges: 445
5.	Protocol: TCP
6.	Action: Allow
7.	Name: AllowSMB
8.	Click Add.
And after this in connect download file RDP that VM and run and paste password and then new window open …after this open VM CMD as adminstartor and then 
go into VM and file storge and 
then select file name and connect and copy script if error came then only use this “net use Z: \\VMNAME.file.core.windows.net\filename /user:AZURE\VMNAME <PASTE_YOUR_NEW_KEY_HERE> (we get new key from storage account then access key)/persistent:yes””

and one disk is created and now form a file in VM nad then chek in azure file shere 
and selet file name and then chek browser…





Vnet::
First we create resourse and then select virtual network in which we add to subnet and give there IP and deploy group.
Then we creat seacurity group for both and then 
Go to each seacurity groub add inbound rule for app nsg in case of app we add source ap addresdd of websubnet.and in case of web we must add 22 port and select ssh in service.
And then same NSG go to subnet and create association .do this for both nsg

Then create 2 VM for both and in network part slect both subnet. and then create VM.. and key download and in connect copy command and run in CMD




Azure APP service:
First create service plan ..and must select OS window and create.
Then go to APP service and create in creation select runtime stack “node 22 lst” and select window and then create. Then go to go resource and copy link.
After this search advance tool. Then go  after this in header select debug consol select CMD and then go into site then go wwwroot then update html file.

Now through VS code 
If you want to use already create then not do this ”First create service plan ..and must select OS window and create.
Then go to APP service and create in creation select runtime stack “node 22 lst” and select window and then create. Then go to go resource and copy link.
then go to vs code and extension is already install then open folder and deploy .go to azure extension. and deploy.



Github:

First create github repository and then vs create a folder and paste html code and then run thses command “
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/Reeha33/mid.git
git push -u origin main


if erroe then do this  
git pull origin main --allow-unrelated-histories
(If this opens a text editor, it is likely the 'vim' editor. Press Esc, then type :wq and press Enter to save and exit).
Again puch “git push -u origin main”

then go to azure and create app service and then go to deployment option and connect github with azure if and main thing in the yml file remove npm run command and other is simple.























# mid
