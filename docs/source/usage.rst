Server Usage Instructions
=========================
This document provides the configuration details to accessing servers available to the Lab RoCoCo, along with usage instructions and guidelines.

Resources
---------
- **Booking Calendar**: The Google Calendar to reserve the machines is available to all the users of the labrococo@diag.uniroma1.it group. When booking a machine, please follow the following booking naming convention:
   
   .. code-block:: bash

      <SURNAME> - <MACHINE-ID>

- **Servers IP Addresses**: `Resources <https://rococo-lounge.readthedocs.io/en/latest/resources.html>`_ 

Policy
------

- **Different Resources for different tasks**: Servers are divided into two categories depending on their computational powers.
  
  - **Proofing Servers**: These servers can be booked for time-slots in the range of hours (maximum 12 straight hours). You can use these machines to launch tests and small-scale experiments in order to verify the correctness of your code. No extensive training should be performed on these machines.
  
  - **Training Servers**: These servers can be booked for time-slots in the range of days (maximum 5 straight days). You can use these machines to launch extensive training sessions and experiments. These machines should always run at maximum computational overload. No proofing should be performed on these machines.

  - **Note**: If by the end of the reservation of a Training Server, there are no other reservations, you can reserve it for additional (maximum) 5 days. You can repeat this process until another user books the machine.

  - **Particular Case**: In the case of the particular Server "Gin", which is equipped with 2 4090 with 24 GB each and 128 GB of RAM, it is possible for 2 people to simultaneously book the Server and run their experiments in parallel. Each person will have access to 1 GPU and 64 GB of RAM. Since we are not able to restrict the use of the resources automatically, we rely on users that exploit this process to be aware on the computational overhead of their training experiments and to not exceed the resources they have been assigned. When booking the Server "Gin", please follow the following booking naming convention:
   .. code-block:: bash

      <SURNAME> - <MACHINE-ID> - <GPU-ID>
   
   The <GPU-ID> is the ID of the GPU you are going to use. It is either "cuda:0" or "cuda:1". Please use in your code the right device name to send tensors to the right GPU. 

- **Docker Policy**: It is mandatory to use a Docker container to run your code to ensure maximum virtualization of the resources.

- **Venv Policy**: No virtual environments are allowed on the servers natively, i.e., conda or python venv. You can use them inside your Docker container.

- **Data Policy**: Do not store any datasets on the server's SSD. Data should only be stored on the HDDs and mounted via volume mappings inside the Docker container. If your dataset is relatively small (<100GB), you are allowed to load it on SSD, but be ready to move it on HDD in case of storage shortage.

- **Cordiality and Respect**: Maintain a positive and respectful atmosphere for shared usage.

- **Experiment Continuity**: Avoid interrupting another user’s experiment, even if it is outside the booking schedule. Always communicate via the labrococo Google group if there’s an issue.

- **Conflict Resolution**: In case of a scheduling conflict, attempt to resolve it privately before taking any actions.

Using the Servers
----------

After a reservation has been made on the calendar, follow these steps to access the server:

1. **Log In**: Connect via SSH using the following command:

   .. code-block:: bash

      ssh <yourUserGroup>@<ipServer>

   - **Username**: the User Group you have to use while connecting to the server depends on your specific affiliation with Lab RoCoCo. If you are a Master Student, use the Group "user". If you are a PhD Student, use the Group "phd_student". If you are a Professor, use the Group "professor".
   - **Password**: inside the Google Calendar description you are going to find the password for the "user" account. For the remaining groups, ask to one of the admin.
   - **NOTE**: It is forbidden to create new personal users on the servers.
   - **Exception**: If there is an European Project or any sort of project that requires multi-role users to cooperate on a single account, please contact the Lab RoCoCo's Admins to create a new user group that will be used specifically for that project.

2. **Check GPU Usage**: Use the following commands to check GPU and server load:

   .. code-block:: bash

      nvidia-smi
      htop

3. **Workspace Directory**: Create a workspace directory for your experiments. This directory will then be mounted and mapped by you to your Docker container workspace directory.

   .. code-block:: bash

      mkdir /home/<yourUserGroup>/SURNAME

Contacts
--------
- **Professor**: iocchi@diag.uniroma1.it
- **Admins**: suriani@diag.uniroma1.it, argenziano@diag.uniroma1.it