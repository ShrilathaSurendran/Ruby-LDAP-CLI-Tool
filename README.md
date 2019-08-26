# Ruby-LDAP-CLI-Tool

# Pre-Requisites
Make sure you run your ldap container in port 1300.

`docker run -p 1300:389 -p 1600:636 --name my-openldap-container --detach osixia/openldap:1.2.4`

Require `thor` gem - https://github.com/erikhuda/thor

Require `net-ldap` gem - https://github.com/ruby-ldap/ruby-net-ldap

# Steps
1. To add the user entries in the LDAP using csv format. You must specify the csv file path as a parameter. CSV file must conain the headers "cn", "sn", "mail", "uid".

    `ruby ldap_csv_tool add path/to/file.csv`
   
   Example: users.csv contains 2 user informations given below. 
   
   `"cn","sn","mail","uid"`
   
   `"Albert","Joe","albert@example.org","albert"`
   
   `"George","Smith","george@example.org","george"`
   
   Command to add users:
	 `$ ruby ldap_csv_tool add "mycomputer/users.csv"`
   
   Result: 
   
   `"Record Albert: 0 => Success"`
   
   `"Record George: 0 => Success"`
   
   `"Added 2 entries."`
   
 
 2. To search the user entries in the LDAP directories. You must specify the Filter query and Ouput csv file path as a parameters.    
    Command to search users:
	 `$ ruby ldap_csv_tool search "uid=albert" "mycomputer/output.csv"`
   
    Result:
    
    `dn: cn=Albert,ou=people,dc=example,dc=org`
    
    `cn: Albert`
    
    `objectclass: inetOrgPerson`
    
    `sn: Joe`
    
    `mail: albert@example.org`
    
    `uid: albert`
    
    `"Exported to /mycomputer/output.csv"`
    
