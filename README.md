# cisco-pro-ig-ig
strimyx!!
LAPTOP

Router>en

Router#conf t

Router(config)#int g2/0

Router(config-if)#no shutdown



Router(config-if)#ip address 192.170.1.1 255.255.255.192

Router(config-if)#line vty 0 4

Router(config-line)#password L

Router(config-line)#login

Router(config-line)#enable secret L
          
	
Router(config-line)#enable secret L
	
Router(config-line)#enable secret Admin

Router(config)#hostname Leo

Leo(config)#ip domain-name irc,com

-------------------------------------------------------------------------------

PC-9 


C:\>telnet 192.170.1.1 

Trying 192.170.1.1 ...Open


User Access Verification

Password: 

Leo>en

Password: 

Leo#conf t

Leo(config)#int g1/0

Leo(config-if)#no shutdown


Leo(config-if)#exit

Leo(config)#int g0/0

Leo(config-if)#no shutdown



Leo(config-if)#exit
	
Leo(config)#exit

Leo#show cdp neighbors detail

Leo#conf t

Leo(config)#int g1/0 

Leo(config-if)#ip address 200.0.0.13 255.255.255.252

Leo(config-if)#exit

Leo(config)#int g0/0

Leo(config-if)#ip address 200.0.0.10 255.255.255.252

Leo(config-if)#exit

Leo(config)#router rip

Leo(config-router)#v 2

Leo(config-router)#no auto-summary

Leo(config-router)#net 200.0.0.8

Leo(config-router)#net 200.0.0.12

Leo(config-router)#net 192.170.1.0

Leo(config-router)#exit

Leo(config)#router ospf 1

Leo(config-router)#net 200.0.0.8 0.0.0.3 area 2

Leo(config-router)#net 200.0.0.12 0.0.0.3 area 2

Leo(config-router)#redistribute rip subnets

Leo(config-router)#exit

Leo(config)#router rip

Leo(config-router)#v 2

Leo(config-router)#redistribute ospf 1 metric 5

Leo(config-router)#exit


-------------------------------------------------------------------------

Ashera!!

✅ Configuration Telnet Cisco - Étapes détaillées
1. 🔌 Connexion initiale au routeur
Depuis le PC, entrer les commandes suivantes :

bash
Copier
Modifier
Router> enable
Router# configure terminal
Router(config)# interface g1/0    
Router(config-if)# no shutdown    // Activer l’interface

--------------------------------------------------------------------
2. 💻 Configuration IP sur le PC9
Vérifier l’adresse IP et le masque du PC9. Exemple :

nginx
Copier
Modifier
Adresse IP : 192.170.1.1
Masque : 255.255.255.192
Configurer le PC :

bash
Copier
Modifier
ip address 192.170.1.1 255.255.255.192

---------------------------------------------------------------------
3. 🔐 Configuration Telnet sur le routeur
Retourner en mode configuration globale :

bash
Copier
Modifier
Router(config)# line vty 0 4            // Créer 5 connexions Telnet
Router(config-line)# password Irc2025   // Définir un mot de passe Telnet
Router(config-line)# login              // Activer la demande de mot de passe
Router(config)# enable secret Admin     // Mot de passe pour enable
Router(config)# hostname Central        // Renommer le routeur
Router(config)# ip domain-name irc,com  // Définir un domaine
---------------------------------------------------------------------------
4. 🖥️ Connexion Telnet depuis le PC9
Dans le terminal du PC9, entrer :

bash
Copier
Modifier
telnet 192.170.1.1
Puis :

Password : Irc2025

Taper : enable

Password : Admin
------------------------------------------------------------------------------
5. 📡 Activer toutes les interfaces + IP des liens
bash
Copier
Modifier
Central# configure terminal
Central(config)# interface g1/0
Central(config-if)# no shutdown
Central(config-if)# exit

Central(config)# interface g2/0
Central(config-if)# no shutdown
Central(config-if)# exit
Afficher les voisins connectés :

bash
Copier
Modifier
Central# show cdp neighbors detail
Repérer les IP connectées :

G1/0 → voisin : 200.0.0.9 → on met : 200.0.0.10

G2/0 → voisin : 200.0.0.14 → on met : 200.0.0.13

Configurer les interfaces avec masque /30 :

bash
Copier
Modifier
Central(config)# interface g1/0
Central(config-if)# ip address 200.0.0.13 255.255.255.252
Central(config-if)# exit

Central(config)# interface g2/0
Central(config-if)# ip address 200.0.0.10 255.255.255.252
Central(config-if)# exit
-------------------------------------------------------------------
6. 🔁 Configuration du Routage RIP et OSPF
RIP :
bash
Copier
Modifier
Central(config)# router rip
Central(config-router)# version 2
Central(config-router)# no auto-summary
Central(config-router)# network 200.0.0.8
Central(config-router)# network 200.0.0.12
Central(config-router)# network 192.170.1.0
Central(config-router)# exit
OSPF :
bash
Copier
Modifier
Central(config)# router ospf 1
Central(config-router)# network 200.0.0.8 0.0.0.3 area 2
Central(config-router)# network 200.0.0.12 0.0.0.3 area 2
Central(config-router)# redistribute rip subnets
Central(config-router)# exit
Redistribution RIP ↔ OSPF :
bash
Copier
Modifier
Central(config)# router rip
Central(config-router)# version 2
Central(config-router)# redistribute ospf 1 metric 5
-------------------------------------------------------------------


