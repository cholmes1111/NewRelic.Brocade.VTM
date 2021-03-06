# Org.BeyondComputing.NewRelic.Brocade.VTM
New Relic plugin for Pulse Virtual Traffic Manager Appliance - previously Brocade

# Requirements
1. .Net 4.5
2. Brocade Virtual Traffic Manager v9.9+, Stingray SteelApp Traffic Manager 9.9+ or Pulse Secure Traffic Manager
3. Traffic Manager API v6.0 by default and for full functionality or version 3.3+ if specified in plugin.json "api_version"

# Known Issues
There is a memory leak in VTM appliances before version 10.1 - SR32022.  This will cause increased memory usage over time based on my own results about 10-20% per month.

# Stats
Device Statistics: CPU %, Memory %, network traffic transmitted / received, connections, device errors, failed nodes
Virtual Servers: Connections, network traffic transmitted / received
Pools: Failed Nodes, Drained nodes, Disabled Nodes, network traffic transmitted / received
Nodes: Requests, Connections, Errors, Failures

# Traffic Manager Configuration
It is highly recommended that you do not use the default or full admin user account, but create a specific account for NewRelic to use.

1. Create a new group for permissions
2. Assign Permissions: 
2a. Advanced Management -> SOAP Control API -> Full
2b. All other Permissions -> Read-Only
3. Create a new User
4. Assign user to previously created group

Certificates - You must use a DNS name when connecting to the load balancer as all communication is sent using HTTPS.  You will also need to have a valid certificate or import the self-signed certificate into the windows cert store on the monitoring box.

# Installation
1. Download release and unzip on machine to handle monitoring.
2. Edit Config Files
    rename newrelic.template.json to newrelic.json
    Rename plugin.template.json to plugin.json
    Update settings in both config files for your environment
3. Run plugin.exe from Command line

Use NPI to install the plugin to register as a service

1. Run Command as admin: npi install org.beyondcomputing.newrelic.brocade.vtm
2. Follow on screen prompts
