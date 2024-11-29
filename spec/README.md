# MountingOrchestrator Specification

The MountingOrchestrator application will handle the mounting of new or changed devices after the field engineer triggers the mounting via APT, which is in turn calling the respective services at the APTP.  

The MountingOrchestrator should also offer the following functionality:
- check mountpoints
- add new mountpoints or edit existing ones
- delete mountpoints
- provide status mounting information (e.g. "10 mounts successful at time x")  and also audit log
- also gather application performance statistics
- indicate that link is ready for link acceptance

### Device Mounting
The MountingOrchestrator needs to carry out the following steps to mount a new or changed device:
1. get the list of mounted devices from the Controller for existing mountpoints and get related information from MediatorManager for comparison
2. do a connection check for the device (ping, snmp - depending on device type)
3. connection preparation via calling the ConnectionPreparation services
4. obtaining the mediator ip and netconf port for mounting the device at the Controller via MediatorManager
5. mount the device on the controllers
   - configuration remains the same for all mountpoints
   - but schema directory will change (model specific or vendor specific) in the future
6. write the mount-name (via MWDG)
7. enable performance-management on the device (via MWDG)
8. update the linkId in the ltp (via LinkIdtoLtpWriter)
9. write MountingOrchestrator performance statistics to the PM app

### Dependencies
The MountingOrchestrator has the following dependencies to other SDN applications:
- [AccessPlanningToolProxy](https://github.com/openBackhaul/AccessPlanningToolProxy)  
- [ConnectionPreparation](https://github.com/openBackhaul/ConnectionPreparation)  
- [MediatorManager](https://github.com/openBackhaul/MediatorManager)  
- [LinkIdIntoLtpWriter](https://github.com/openBackhaul/LinkIdIntoLtpWriter)  
- [MicroWaveDeviceGatekeeper](https://github.com/openBackhaul/MicroWaveDeviceGatekeeper)  
- [PerformanceManagement](https://github.com/openBackhaul/PerformanceManagement)  
- [MicroWaveDeviceInventory](https://github.com/openBackhaul/MicroWaveDeviceInventory)  
- ODL Controller

### ServiceList
- [MountingOrchestrator+services](./MountingOrchestrator+services.yaml)

### ProfileList and ProfileInstanceList
- [MountingOrchestrator+profiles](./MountingOrchestrator+profiles.yaml)
- [MountingOrchestrator+profileInstances](./MountingOrchestrator+profileInstances.yaml)

### ForwardingList
- [MountingOrchestrator+forwardings](./MountingOrchestrator+forwardings.yaml)

### Open API specification (Swagger)
- [MountingOrchestrator](./MountingOrchestrator.yaml)

### CONFIGfile (JSON)
- [MountingOrchestrator+config](./MountingOrchestrator+config.json)

### Comments
./.
