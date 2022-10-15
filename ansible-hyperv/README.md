- name: Manage Hyper-V
  hosts:
    - yourservername
  tasks:
    - name: Create test.example.com VM
      win_hyperv_guest:
        name: test.example.com
        generation: 1
        memory: 256MB
        network_switch: WAN1
        state: present
    - name: Remove old.example.com VM
      win_hyperv_guest:
        name: old.example.com
    state: absent

Example
vms:
  - type: testserver
    name: "nicktest"

    cpu: 2   
    memory: 4096MB

    network:
      ip: 192.168.23.26
      netmask: 255.255.255.0
      gateway: 192.168.23.254
      dns: 192.168.0.17,192.168.0.18
      
#    network_switch: 'External Virtual Switch'
    network_switch: 'Cisco VIC Ethernet Interface #6 - Virtual Switch'
    vlanid: 1113 

    src_vhd: 'C:\volumes\devops\devopssysprep\devopssysprep.vhdx'
    dest_vhd: 'C:\volumes\devops\nicktest.vhdx'