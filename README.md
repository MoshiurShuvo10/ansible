# Ansible

## Install Ansible
* Create a inventory.txt file in ansible controller. target1 is the domain name, ansible_host, ansible_ssh_pass is attribute.

   ```target1 ansible_host=<ip_of_target> ansible_ssh_pass=<password_of_target>```
* Now check if ansible controller can connect to target 1

  ``` ansible target1 -m ping -i inventory.txt```

* If any error occurs like "Host key checking is enabled........ Please add host's fingerprint to known_hosts file to manage this host" -- There are two ways to fix this.
  - Approach 1 (NOT RECOMMENDED): disable **host_key_checking** flag in **/etc/ansible/ansible.cfg** file
  - Approach 2: ssh-copy-id

<hr><hr>

## YAML Syntax
* Key Value pair: A space is mandatory before the value (after the colon ( : ))

	```
	Fruit: Apple
	Vegetable: Carrot
	Liquid: Water
		
	```

* Array / Lists : Fruits, Vegetables are two arrays. Array elements are represented by dash ( - )

	```
	Fruits:
	- Apple
	- Orange
	- Bannana

	Vegetables:
	- Carrot
	- Tomato
	```

* Dictionary / Map : Equal number of space is mandatory before each value.

	```
	Banana:
	Calories: 105
	Fat: 0.4 g
	Carbs: 27 g

	Grapes:
	Calories: 62
	Fat: 0.3 g
	```

* List is Ordered collection. In the below example of two lists, content are same, but orders are not same. Thats why they are two different collection.s
  
	```
	Fruits:
	- Orange
	- Banana
	```

	```
	Fruits:
	- Banana
	- Orange
	```
* Dictionary is unordered collection. Below mentioned two dictionaries are same even though their orders are not same.

	```
	Banana:
		calories: 103
		color: yellow
	```

	```
	Banana:
		color: yellow
		calories: 103
	```
<hr><hr>

## Inventory 
* Information about target machines are stored in inventory file. If we don't specify any inventory file, ansible picks the default inventory file which is /etc/ansible/hosts file.
* Inventy parameters: 
  - **ansible_connection:** Defines how ansible connects to the target server. ssh for linux target server, winrm for windows target server.
  - **ansible_port:** Defines in which port of target ansible controller should connect to. 
  - **ansible_user** Defines which user makes the ruquest to the remote server. root for linux, admin for windows.
  - **ansible_ssh_pass** SSH password for linux.
* Sample inventory file
	```
	web ansible_host=server1.com ansible_connection=ssh 
	db ansible_host=server2.com ansible_connection=winrm
	mail ansible_host=mailserver.com ansible_connection=ssh
	```
<hr><hr>

## Ansible Playbook
* Playbook: A single yml file
* Play: A set of tasks to be run on the target
* Task: An action to be performed on the target.

