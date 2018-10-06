1. Setup Accounts

	1.) Plotly
		a. Create account at http://plot.ly
		b. Generate API Key on website
		c. Enter user name and API key in python script Credential.py

	2.) Nest
		a. Create nest account
		b. Link Nest thermostat
	
	3.) Forecast.IO
	
	4.) Wemo
		a. Setup Wemo switch with Wemo app	

2. Set timezone to PST permanently by adding to /home/pi/.profile

	a. enter "echo "TZ='America/Los_Angeles'; export TZ" >.profile"
	b. enter "sudo raspi-config"
	c. Select Internationalisation Options->Change Timezone

3. 	Enable I2C interface
	a. enter "sudo raspi-config"
	b. Select Advanced Options->I2C and enable I2C interface and load I2C kernel module

4. Install libraries
	a. enter "sudo apt-get update"
	b. enter "sudo apt-get install python-pip python-dev mysql-server libmysqlclient-dev samba samba-common-bin git build-essential i2c-tools python-smbus"
	c. enter "sudo pip install plotly MySQL-python"
	d. enter "sudo easy_install ouimeaux"
	e. enter "git clone https://github.com/adafruit/Adafruit_Python_BMP.git"
	f. enter "cd Adafruit_Python_BMP"
	g. enter "sudo python setup.py install"

5. 	Setup Samba
	a. Add user pi
	b. enter "sudo smbpasswd -a pi"
	c. Edit samba config file
	d. enter "sudo nano /etc/samba/smb.conf"
	e. Uncomment these lines:
		security = user
		socket options = TCP_NODELAY

	f. Update these lines:
		[homes]
			comment = Home Directories
			browseable = no
			read only = no

	g. Check for errors in config file
		testparm		
	h. Restart samba server
	i. enter "sudo /etc/init.d/samba restart"

6. Setup BMP180 pressure sensor
	Append to file:
	a. enter "sudo nano /etc/modules"
	b. i2c-bcm2708
	c. i2c-dev
	d. enter "git clone https://github.com/adafruit/Adafruit_Python_BMP.git"
	e. enter "cd Adafruit_Python_BMP"
	f. enter "sudo python setup.py install"


7. Setup MySQL
	a. enter "mysql_secure_installation"
	b. Create database
	c. enter "mysql -u root -p"
	d. enter "create database home_automation;"
	
8. Run python script at startup
	a. Create startup script
	b. enter "nano ~/startup.sh"
	c. enter "sudo python /home/pi/HomeWeather/HomeWeather.py"
	d. Add line to /etc/rc.local before exit 0
	e. enter "sudo sh /home/pi/startup.sh"
