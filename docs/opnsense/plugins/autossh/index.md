# AutoSSH (autossh) for OPNsense

AutoSSH for OPNsense is (currently) an older OPNsense plugin originally created by 
Nicholas de Jong and no longer works with current versions of OPNsense.

We are working on getting this plugin up-to-date, tested and published through the 
Threat Patrols repo packaging pipeline.

## Github
* https://github.com/threatpatrols/opnsense-plugin-autossh



<!---
                
    <h2>Features</h2>
    <ul>
        <li>Default ssh-keys provided with shell-prevention restrictions to prevent unwanted remote shell access.</li>
        <li>Ability to define local-forward, remote-forward and SOCKS proxy-forwards.</li>
        <li>Ability to bind outbound ssh connections to specific interfaces.</li>
        <li>Ability to configure many of the ssh-client connection parameters, including all cryptographic options.</li>
        <li>Ability to observe the health status of a tunnel at a glance.</li>
        <li>Rely on autossh to reestablish a tunnel after a connectivity disruption.</li>
    </ul>
    
    <h2>Various use cases</h2>
    <ul>
        <li>Provide remote network access to a site that has no public addresses, such as when ISPs use NAT.</li>
        <li>Ensure redundant multipath remote access via primary and secondary connections via interface binding.</li>
        <li>Create your own "privacy" VPN system for all local network users using a SOCKS proxy (dynamic-forward) to a remote system.</li>
        <li>Provide local network access to remote system services such as a SMTP relay or another SSH service.</li>
        <li>Provide remote system access to a local network services such as a database or RDP service.</li>
        <li>Provide access remote system access to other remote network acting as a middle-man TCP-port connector.</li>
    </ul>

    <h2>Tunnel configuration</h2>
    <h3>Local Forward</h3>
    <p>
        Describe how to expose a remote TCP port into the local network
    </p>
    
    <h3>Remote Forward</h3>
    <p>
        Describe how to expose a TCP port in the local network at a remote system
    </p>
    
    <h3>Dynamic Forward</h3>
    <p>
        Describe how to write an expression that creates a SOCKS proxy for the local network
    </p>
    
    <h3>Gateway Ports</h3>
    <p>
        Describe the situations where this is important and required
    </p>
    
    <h3>Strict Host Key Checking</h3>
    <p>
        Describe what this is all about and the interaction with the "Update Host Keys" property
    </p>
    
    <h2>Key management</h2>
    <h3>Private Key</h3>
    <p>
        Describe how keys are stored and the potential risks
        Describe the key types and the sometimes limited support for newer key types
    </p>
    
    <h3>Public Key</h3>
    <p>
        Describe how to access it
        Describe the importance of the key permission prefix to prevent abuse
        Describe where to place the public key value on the remote system
    </p>
    
    <h3>External Keys</h3>
    <p>
        Describe that no external keys are currently possible as a matter of preventing unwanted problem scenarios
        Willing to listen to feedback and introduce a key import feature if warranted
    </p>
    
    <h2>Connection status</h2>
    <p>
        Notes about forwards
        Description of status attributes
        Describe the autossh health check with a "ping" every minute
    </p>

--->
