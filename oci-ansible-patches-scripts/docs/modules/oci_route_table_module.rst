:source: cloud/oracle/oci_route_table.py

:orphan:

.. _oci_route_table_module:


oci_route_table - Create,update and delete OCI Route Table
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.5

.. contents::
   :local:
   :depth: 2


Synopsis
--------
- Creates OCI Route Table
- Update OCI Route Table, if present, with a new display name
- Update OCI Route Table, if present, by appending new Route Rules to existing Route Rules
- Update OCI Route Table, if present, by purging existing Route Rules and replacing them with specified ones
- Delete OCI Route Table, if present.



Requirements
~~~~~~~~~~~~
The below requirements are needed on the host that executes this module.

- python >= 2.6
- Python SDK for Oracle Cloud Infrastructure https://oracle-cloud-infrastructure-python-sdk.readthedocs.io


Parameters
----------

.. raw:: html

    <table  border=0 cellpadding=0 class="documentation-table">
        <tr>
            <th colspan="2">Parameter</th>
            <th>Choices/<font color="blue">Defaults</font></th>
                        <th width="100%">Comments</th>
        </tr>
                    <tr>
                                                                <td colspan="2">
                    <b>api_user</b>
                                                                            </td>
                                <td>
                                                                                                                                                            </td>
                                                                <td>
                                                                        <div>The OCID of the user, on whose behalf, OCI APIs are invoked. If not set, then the value of the OCI_USER_OCID environment variable, if any, is used. This option is required if the user is not specified through a configuration file (See <code>config_file_location</code>). To get the user's OCID, please refer <a href='https://docs.us-phoenix-1.oraclecloud.com/Content/API/Concepts/apisigningkey.htm'>https://docs.us-phoenix-1.oraclecloud.com/Content/API/Concepts/apisigningkey.htm</a>.</div>
                                                                                </td>
            </tr>
                                <tr>
                                                                <td colspan="2">
                    <b>api_user_fingerprint</b>
                                                                            </td>
                                <td>
                                                                                                                                                            </td>
                                                                <td>
                                                                        <div>Fingerprint for the key pair being used. If not set, then the value of the OCI_USER_FINGERPRINT environment variable, if any, is used. This option is required if the key fingerprint is not specified through a configuration file (See <code>config_file_location</code>). To get the key pair's fingerprint value please refer <a href='https://docs.us-phoenix-1.oraclecloud.com/Content/API/Concepts/apisigningkey.htm'>https://docs.us-phoenix-1.oraclecloud.com/Content/API/Concepts/apisigningkey.htm</a>.</div>
                                                                                </td>
            </tr>
                                <tr>
                                                                <td colspan="2">
                    <b>api_user_key_file</b>
                                                                            </td>
                                <td>
                                                                                                                                                            </td>
                                                                <td>
                                                                        <div>Full path and filename of the private key (in PEM format). If not set, then the value of the OCI_USER_KEY_FILE variable, if any, is used. This option is required if the private key is not specified through a configuration file (See <code>config_file_location</code>). If the key is encrypted with a pass-phrase, the <code>api_user_key_pass_phrase</code> option must also be provided.</div>
                                                                                </td>
            </tr>
                                <tr>
                                                                <td colspan="2">
                    <b>api_user_key_pass_phrase</b>
                                                                            </td>
                                <td>
                                                                                                                                                            </td>
                                                                <td>
                                                                        <div>Passphrase used by the key referenced in <code>api_user_key_file</code>, if it is encrypted. If not set, then the value of the OCI_USER_KEY_PASS_PHRASE variable, if any, is used. This option is required if the key passphrase is not specified through a configuration file (See <code>config_file_location</code>).</div>
                                                                                </td>
            </tr>
                                <tr>
                                                                <td colspan="2">
                    <b>auth_type</b>
                                                                            </td>
                                <td>
                                                                                                                            <ul><b>Choices:</b>
                                                                                                                                                                <li><div style="color: blue"><b>api_key</b>&nbsp;&larr;</div></li>
                                                                                                                                                                                                <li>instance_principal</li>
                                                                                    </ul>
                                                                            </td>
                                                                <td>
                                                                        <div>The type of authentication to use for making API requests. By default <code>auth_type=&quot;api_key&quot;</code> based authentication is performed and the API key (see <em>api_user_key_file</em>) in your config file will be used. If this 'auth_type' module option is not specified, the value of the OCI_ANSIBLE_AUTH_TYPE, if any, is used. Use <code>auth_type=&quot;instance_principal&quot;</code> to use instance principal based authentication when running ansible playbooks within an OCI compute instance.</div>
                                                                                </td>
            </tr>
                                <tr>
                                                                <td colspan="2">
                    <b>compartment_id</b>
                                                                            </td>
                                <td>
                                                                                                                                                            </td>
                                                                <td>
                                                                        <div>Identifier of the compartment under which this Route Table would be created. Mandatory for create operation.Optional for delete and update. Mutually exclusive with rt_id.</div>
                                                                                </td>
            </tr>
                                <tr>
                                                                <td colspan="2">
                    <b>config_file_location</b>
                                                                            </td>
                                <td>
                                                                                                                                                            </td>
                                                                <td>
                                                                        <div>Path to configuration file. If not set then the value of the OCI_CONFIG_FILE environment variable, if any, is used. Otherwise, defaults to ~/.oci/config.</div>
                                                                                </td>
            </tr>
                                <tr>
                                                                <td colspan="2">
                    <b>config_profile_name</b>
                                                                            </td>
                                <td>
                                                                                                                                                                    <b>Default:</b><br/><div style="color: blue">DEFAULT</div>
                                    </td>
                                                                <td>
                                                                        <div>The profile to load from the config file referenced by <code>config_file_location</code>. If not set, then the value of the OCI_CONFIG_PROFILE environment variable, if any, is used. Otherwise, defaults to the &quot;DEFAULT&quot; profile in <code>config_file_location</code>.</div>
                                                                                </td>
            </tr>
                                <tr>
                                                                <td colspan="2">
                    <b>defined_tags</b>
                                                                            </td>
                                <td>
                                                                                                                                                            </td>
                                                                <td>
                                                                        <div>Defined tags for this resource. Each key is predefined and scoped to a namespace. For more information, see <a href='https://docs.us-phoenix-1.oraclecloud.com/Content/General/Concepts/resourcetags.htm'>https://docs.us-phoenix-1.oraclecloud.com/Content/General/Concepts/resourcetags.htm</a>.</div>
                                                                                </td>
            </tr>
                                <tr>
                                                                <td colspan="2">
                    <b>delete_route_rules</b>
                    <br/><div style="font-size: small; color: red">bool</div>                                                        </td>
                                <td>
                                                                                                                                                                        <ul><b>Choices:</b>
                                                                                                                                                                <li><div style="color: blue"><b>no</b>&nbsp;&larr;</div></li>
                                                                                                                                                                                                <li>yes</li>
                                                                                    </ul>
                                                                            </td>
                                                                <td>
                                                                        <div>Delete route rules in existing Route Table which are present in the provided Route Rules. If <em>delete_route_rules=yes</em>, route rules provided by <em>route_rules</em> would be deleted from existing route rules, if they are part of existing route rules. If they are not part of existing route rules, they will be ignored. <em>delete_route_rules</em> and <em>purge_route_rules</em> are mutually exclusive.</div>
                                                                                </td>
            </tr>
                                <tr>
                                                                <td colspan="2">
                    <b>display_name</b>
                                                                            </td>
                                <td>
                                                                                                                                                            </td>
                                                                <td>
                                                                        <div>Name of the Route Table. A user friendly name. Does not have to be unique, and could be changed. If not specified, a default name would be provided.</div>
                                                                                        <div style="font-size: small; color: darkgreen"><br/>aliases: name</div>
                                    </td>
            </tr>
                                <tr>
                                                                <td colspan="2">
                    <b>force_create</b>
                    <br/><div style="font-size: small; color: red">bool</div>                                                        </td>
                                <td>
                                                                                                                                                                                                                    <ul><b>Choices:</b>
                                                                                                                                                                <li><div style="color: blue"><b>no</b>&nbsp;&larr;</div></li>
                                                                                                                                                                                                <li>yes</li>
                                                                                    </ul>
                                                                            </td>
                                                                <td>
                                                                        <div>Whether to attempt non-idempotent creation of a resource. By default, create resource is an idempotent operation, and doesn't create the resource if it already exists. Setting this option to true, forcefully creates a copy of the resource, even if it already exists.This option is mutually exclusive with <em>key_by</em>.</div>
                                                                                </td>
            </tr>
                                <tr>
                                                                <td colspan="2">
                    <b>freeform_tags</b>
                                                                            </td>
                                <td>
                                                                                                                                                            </td>
                                                                <td>
                                                                        <div>Free-form tags for this resource. Each tag is a simple key-value pair with no predefined name, type, or namespace. For more information, see <a href='https://docs.us-phoenix-1.oraclecloud.com/Content/General/Concepts/resourcetags.htm'>https://docs.us-phoenix-1.oraclecloud.com/Content/General/Concepts/resourcetags.htm</a>.</div>
                                                                                </td>
            </tr>
                                <tr>
                                                                <td colspan="2">
                    <b>key_by</b>
                                                                            </td>
                                <td>
                                                                                                                                                            </td>
                                                                <td>
                                                                        <div>The list of comma-separated attributes of this resource which should be used to uniquely identify an instance of the resource. By default, all the attributes of a resource except <em>freeform_tags</em> are used to uniquely identify a resource.</div>
                                                                                </td>
            </tr>
                                <tr>
                                                                <td colspan="2">
                    <b>purge_route_rules</b>
                    <br/><div style="font-size: small; color: red">bool</div>                                                        </td>
                                <td>
                                                                                                                                                                        <ul><b>Choices:</b>
                                                                                                                                                                <li>no</li>
                                                                                                                                                                                                <li><div style="color: blue"><b>yes</b>&nbsp;&larr;</div></li>
                                                                                    </ul>
                                                                            </td>
                                                                <td>
                                                                        <div>Purge route rules in existing Route Table which are not present in the provided Route Rules. If <em>purge_route_rules=no</em>, provided route rules would be appended to existing route rules. <em>purge_route_rules</em> and <em>delete_route_rules</em> are mutually exclusive.</div>
                                                                                </td>
            </tr>
                                <tr>
                                                                <td colspan="2">
                    <b>region</b>
                                                                            </td>
                                <td>
                                                                                                                                                            </td>
                                                                <td>
                                                                        <div>The Oracle Cloud Infrastructure region to use for all OCI API requests. If not set, then the value of the OCI_REGION variable, if any, is used. This option is required if the region is not specified through a configuration file (See <code>config_file_location</code>). Please refer to <a href='https://docs.us-phoenix-1.oraclecloud.com/Content/General/Concepts/regions.htm'>https://docs.us-phoenix-1.oraclecloud.com/Content/General/Concepts/regions.htm</a> for more information on OCI regions.</div>
                                                                                </td>
            </tr>
                                <tr>
                                                                <td colspan="2">
                    <b>route_rules</b>
                                                                            </td>
                                <td>
                                                                                                                                                            </td>
                                                                <td>
                                                                        <div>List containing dictionaries describing a route rule. Suboptions should be the CIDR block which is destination ip address in CIDR notation and the identifier of the target entity such as Internet Getway.</div>
                                                                                </td>
            </tr>
                                                            <tr>
                                                    <td class="elbow-placeholder"></td>
                                                <td colspan="1">
                    <b>cidr_block</b>
                                                                            </td>
                                <td>
                                                                                                                                                            </td>
                                                                <td>
                                            <div>A destination IP address range in CIDR notation. Matching packets will be routed to the indicated network entity (the target). This option is deprecated, use destination and destination_type instead.</div>
                                                        </td>
            </tr>
                                <tr>
                                                    <td class="elbow-placeholder"></td>
                                                <td colspan="1">
                    <b>destination</b>
                                                                            </td>
                                <td>
                                                                                                                                                            </td>
                                                                <td>
                                            <div>Conceptually, this is the range of IP addresses used for matching when routing traffic. Required if you provide a destination_type. Allowed values are, IP address range in CIDR notation (For example, 192.168.1.0/24) or The cidr_block value for a service, if you're setting up a route rule for traffic destined for a particular service through a service gateway (For example, oci-phx-objectstorage).</div>
                                                        </td>
            </tr>
                                <tr>
                                                    <td class="elbow-placeholder"></td>
                                                <td colspan="1">
                    <b>network_entity_id</b>
                                        <br/><div style="font-size: small; color: red">required</div>                                    </td>
                                <td>
                                                                                                                                                            </td>
                                                                <td>
                                            <div>The identifier for the target of route rules, such as identifier of the Internet Gateway or Service Gateway.</div>
                                                        </td>
            </tr>
                                <tr>
                                                    <td class="elbow-placeholder"></td>
                                                <td colspan="1">
                    <b>destination_type</b>
                                                                            </td>
                                <td>
                                                                                                                            <ul><b>Choices:</b>
                                                                                                                                                                <li>CIDR_BLOCK</li>
                                                                                                                                                                                                <li>SERVICE_CIDR_BLOCK</li>
                                                                                    </ul>
                                                                            </td>
                                                                <td>
                                            <div>Type of destination for the rule. Required if you provide a destination. If the rule's destination is an IP address range in CIDR notation, the value should be CIDR_BLOCK.If the rule's destination is the cidr_block value for a service, the value should be SERVICE_CIDR_BLOCK.</div>
                                                        </td>
            </tr>
                    
                                                <tr>
                                                                <td colspan="2">
                    <b>rt_id</b>
                                                                            </td>
                                <td>
                                                                                                                                                            </td>
                                                                <td>
                                                                        <div>Identifier of the Route Table. Mandatory for delete and update, if compartment_id and vcn_id is not specified. Mutually exclusive with compartment_id and vcn_id.</div>
                                                                                        <div style="font-size: small; color: darkgreen"><br/>aliases: id</div>
                                    </td>
            </tr>
                                <tr>
                                                                <td colspan="2">
                    <b>state</b>
                                                                            </td>
                                <td>
                                                                                                                            <ul><b>Choices:</b>
                                                                                                                                                                <li><div style="color: blue"><b>present</b>&nbsp;&larr;</div></li>
                                                                                                                                                                                                <li>absent</li>
                                                                                    </ul>
                                                                            </td>
                                                                <td>
                                                                        <div>Create,update or delete Route Table. For <em>state=present</em>, if it does not exist, it gets created. If it exists, it gets updated.</div>
                                                                                </td>
            </tr>
                                <tr>
                                                                <td colspan="2">
                    <b>tenancy</b>
                                                                            </td>
                                <td>
                                                                                                                                                            </td>
                                                                <td>
                                                                        <div>OCID of your tenancy. If not set, then the value of the OCI_TENANCY variable, if any, is used. This option is required if the tenancy OCID is not specified through a configuration file (See <code>config_file_location</code>). To get the tenancy OCID, please refer <a href='https://docs.us-phoenix-1.oraclecloud.com/Content/API/Concepts/apisigningkey.htm'>https://docs.us-phoenix-1.oraclecloud.com/Content/API/Concepts/apisigningkey.htm</a></div>
                                                                                </td>
            </tr>
                                <tr>
                                                                <td colspan="2">
                    <b>vcn_id</b>
                                                                            </td>
                                <td>
                                                                                                                                                            </td>
                                                                <td>
                                                                        <div>Identifier of the Virtual Cloud Network to which the Route Table should be attached. Mandatory for create operation. Optional for delete and update. Mutually exclusive with rt_id.</div>
                                                                                </td>
            </tr>
                                <tr>
                                                                <td colspan="2">
                    <b>wait</b>
                    <br/><div style="font-size: small; color: red">bool</div>                                                        </td>
                                <td>
                                                                                                                                                                                                                    <ul><b>Choices:</b>
                                                                                                                                                                <li>no</li>
                                                                                                                                                                                                <li><div style="color: blue"><b>yes</b>&nbsp;&larr;</div></li>
                                                                                    </ul>
                                                                            </td>
                                                                <td>
                                                                        <div>Whether to wait for create or delete operation to complete.</div>
                                                                                </td>
            </tr>
                                <tr>
                                                                <td colspan="2">
                    <b>wait_timeout</b>
                                                                            </td>
                                <td>
                                                                                                                                                                    <b>Default:</b><br/><div style="color: blue">1200</div>
                                    </td>
                                                                <td>
                                                                        <div>Time, in seconds, to wait when <em>wait=yes</em>.</div>
                                                                                </td>
            </tr>
                                <tr>
                                                                <td colspan="2">
                    <b>wait_until</b>
                                                                            </td>
                                <td>
                                                                                                                                                            </td>
                                                                <td>
                                                                        <div>The lifecycle state to wait for the resource to transition into when <em>wait=yes</em>. By default, when <em>wait=yes</em>, we wait for the resource to get into ACTIVE/ATTACHED/AVAILABLE/PROVISIONED/ RUNNING applicable lifecycle state during create operation &amp; to get into DELETED/DETACHED/ TERMINATED lifecycle state during delete operation.</div>
                                                                                </td>
            </tr>
                        </table>
    <br/>


Notes
-----

.. note::
    - For OCI python sdk configuration, please refer to https://oracle-cloud-infrastructure-python-sdk.readthedocs.io/en/latest/configuration.html


Examples
--------

.. code-block:: yaml+jinja

    
    # Note: These examples do not set authentication details.
    # Create/update Route Table
    - name: Create a Route Table with a route rule
      oci_route_table:
        compartment_id: 'ocid1.compartment..xxxxxEXAMPLExxxxx'
        vcn_id: 'ocid1.vcn..xxxxxEXAMPLExxxxx'
        name: 'ansible_route_table'
        route_rules:
            - cidr_block: '10.0.0.0/8'
              network_entity_id: 'ocid1.internetgateway..xxxxxEXAMPLExxxxx'
            - destination: 'oci-phx-objectstorage'
              destination_type: 'SERVICE_CIDR_BLOCK'
              network_entity_id: 'ocid1.servicegateway..xxxxxEXAMPLExxxxx'
        freeform_tags:
            region: 'east'
        defined_tags:
            features:
               capacity: 'medium'
        state: 'present'

    # Update Route Table with rt id
    - name: Update the display name of a Route Table
      oci_route_table:
        rt_id: 'ocid1.routetable..xxxxxEXAMPLExxxxx'
        display_name: 'ansible_route_table_updated'
        state: 'present'

    # Update a route table with a new set of route rules,
    # and purge any existing route rules that is not in the
    # specified set of route rules.
    - name: Update a Route Table with purge route rules
      oci_route_table:
        rt_id: 'ocid1.routetable..xxxxxEXAMPLExxxxx'
        purge_route_rules: 'yes'
        route_rules:
            - cidr_block: '10.0.0.0/12'
              network_entity_id: 'ocid1.internetgateway..abcd'
        state: 'present'

    - name: Update a Route Table by deleting route rules
      oci_route_table:
        rt_id: 'ocid1.routetable..xxxxxEXAMPLExxxxx'
        delete_route_rules: 'yes'
        route_rules:
            - cidr_block: '10.0.0.0/12'
              network_entity_id: 'ocid1.internetgateway..abcd'
        state: 'present'

    # Delete Route Table
    - name: Delete Route Table
      oci_route_table:
        rt_id: 'ocid1.routetable..xxxxxEXAMPLExxxxx'
        state: 'absent'




Return Values
-------------
Common return values are documented :ref:`here <common_return_values>`, the following are the fields unique to this module:

.. raw:: html

    <table border=0 cellpadding=0 class="documentation-table">
        <tr>
            <th colspan="2">Key</th>
            <th>Returned</th>
            <th width="100%">Description</th>
        </tr>
                    <tr>
                                <td colspan="2">
                    <b>route_table</b>
                    <br/><div style="font-size: small; color: red">complex</div>
                                    </td>
                <td>success</td>
                <td>
                                            <div>Attributes of the created/updated Route Table. For delete, deleted Route Table description will be returned.</div>
                                        <br/>
                                            <div style="font-size: smaller"><b>Sample:</b></div>
                                                <div style="font-size: smaller; color: blue; word-wrap: break-word; word-break: break-all;">{'lifecycle_state': 'AVAILABLE', 'display_name': 'ansible_route_table', 'compartment_id': 'ocid1.compartment.oc1..xxxxxEXAMPLExxxxx', 'vcn_id': 'ocid1.vcn.oc1.phx.xxxxxEXAMPLExxxxx', 'route_rules': [{'cidr_block': '0.0.0.0/0', 'destination': '0.0.0.0', 'network_entity_id': 'ocid1.internetgateway.oc1.phx.xxxxxEXAMPLExxxxx', 'destination_type': 'CIDR_BLOCK'}, {'cidr_block': None, 'destination': 'oci-phx-objectstorage', 'network_entity_id': 'ocid1.servicegateway.oc1.phx.xxxxxEXAMPLExxxxx', 'destination_type': 'SERVICE_CIDR_BLOCK'}], 'defined_tags': {'features': {'capacity': 'medium'}}, 'freeform_tags': {'region': 'east'}, 'time_created': '2017-11-17T17:39:33.190000+00:00', 'id': 'ocid1.routetable.oc1.phx.xxxxxEXAMPLExxxxx'}</div>
                                    </td>
            </tr>
                                                            <tr>
                                    <td class="elbow-placeholder">&nbsp;</td>
                                <td colspan="1">
                    <b>vcn_id</b>
                    <br/><div style="font-size: small; color: red">string</div>
                                    </td>
                <td>always</td>
                <td>
                                            <div>Identifier of the Virtual Cloud Network to which the Route Table is attached.</div>
                                        <br/>
                                            <div style="font-size: smaller"><b>Sample:</b></div>
                                                <div style="font-size: smaller; color: blue; word-wrap: break-word; word-break: break-all;">ocid1.vcn..ixcd</div>
                                    </td>
            </tr>
                                <tr>
                                    <td class="elbow-placeholder">&nbsp;</td>
                                <td colspan="1">
                    <b>display_name</b>
                    <br/><div style="font-size: small; color: red">string</div>
                                    </td>
                <td>always</td>
                <td>
                                            <div>Name assigned to the Route Table during creation</div>
                                        <br/>
                                            <div style="font-size: smaller"><b>Sample:</b></div>
                                                <div style="font-size: smaller; color: blue; word-wrap: break-word; word-break: break-all;">ansible_route_table</div>
                                    </td>
            </tr>
                                <tr>
                                    <td class="elbow-placeholder">&nbsp;</td>
                                <td colspan="1">
                    <b>compartment_id</b>
                    <br/><div style="font-size: small; color: red">string</div>
                                    </td>
                <td>always</td>
                <td>
                                            <div>The identifier of the compartment containing the Route Table</div>
                                        <br/>
                                            <div style="font-size: smaller"><b>Sample:</b></div>
                                                <div style="font-size: smaller; color: blue; word-wrap: break-word; word-break: break-all;">ocid1.compartment.oc1.xzvf..oifds</div>
                                    </td>
            </tr>
                                <tr>
                                    <td class="elbow-placeholder">&nbsp;</td>
                                <td colspan="1">
                    <b>lifecycle_state</b>
                    <br/><div style="font-size: small; color: red">string</div>
                                    </td>
                <td>always</td>
                <td>
                                            <div>The current state of the Route Table</div>
                                        <br/>
                                            <div style="font-size: smaller"><b>Sample:</b></div>
                                                <div style="font-size: smaller; color: blue; word-wrap: break-word; word-break: break-all;">AVAILABLE</div>
                                    </td>
            </tr>
                                <tr>
                                    <td class="elbow-placeholder">&nbsp;</td>
                                <td colspan="1">
                    <b>route_rules</b>
                    <br/><div style="font-size: small; color: red">string</div>
                                    </td>
                <td>always</td>
                <td>
                                            <div>The collection of rules for routing destination IPs to network devices.</div>
                                        <br/>
                                            <div style="font-size: smaller"><b>Sample:</b></div>
                                                <div style="font-size: smaller; color: blue; word-wrap: break-word; word-break: break-all;">[{'cidr_block': '0.0.0.0/0', 'destination': '0.0.0.0', 'network_entity_id': 'ocid1.internetgateway.xxxxxEXAMPLExxxxx', 'destination_type': 'CIDR_BLOCK'}]</div>
                                    </td>
            </tr>
                                <tr>
                                    <td class="elbow-placeholder">&nbsp;</td>
                                <td colspan="1">
                    <b>id</b>
                    <br/><div style="font-size: small; color: red">string</div>
                                    </td>
                <td>always</td>
                <td>
                                            <div>Identifier of the Route Table</div>
                                        <br/>
                                            <div style="font-size: smaller"><b>Sample:</b></div>
                                                <div style="font-size: smaller; color: blue; word-wrap: break-word; word-break: break-all;">ocid1.routetable.oc1.axdf</div>
                                    </td>
            </tr>
                                <tr>
                                    <td class="elbow-placeholder">&nbsp;</td>
                                <td colspan="1">
                    <b>time_created</b>
                    <br/><div style="font-size: small; color: red">datetime</div>
                                    </td>
                <td>always</td>
                <td>
                                            <div>Date and time when the Route Table was created, in the format defined by RFC3339</div>
                                        <br/>
                                            <div style="font-size: smaller"><b>Sample:</b></div>
                                                <div style="font-size: smaller; color: blue; word-wrap: break-word; word-break: break-all;">2016-08-25 21:10:29.600000</div>
                                    </td>
            </tr>
                    
                                        </table>
    <br/><br/>


Status
------



This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.



Author
~~~~~~

- Debayan Gupta(@debayan_gupta)


.. hint::
    If you notice any issues in this documentation you can `edit this document <https://github.com/ansible/ansible/edit/devel/lib/ansible/modules/cloud/oracle/oci_route_table.py?description=%3C!---%20Your%20description%20here%20--%3E%0A%0A%2Blabel:%20docsite_pr>`_ to improve it.
