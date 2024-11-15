Server Usage Instructions
=========================
This document provides the configuration details to accessing servers available to Lab RoCoCo's PhD students, along with usage instructions and guidelines.

Resources
---------
- **Booking Calendar**: The Google Calendar to reserve the machines is available to all the users of the labrococo@diag.uniroma1.it group. When booking a machine, please follow the following booking naming convention:
   
   .. code-block:: bash

      <SURNAME> - <MACHINE-ID> - <START TIME> - <END TIME>

- **Servers IP Addresses**: `Resources <https://rococo-lounge.readthedocs.io/en/latest/resources.html>`_ 

Policy
------

- **Different Resources for different tasks**: Servers are divided into two categories depending on their computational powers.
  
  - **Proofing Servers**: These servers can be booked for time-slots in the range of hours (maximum 12 straight hours). You can use these machines to launch tests and small-scale experiments in order to verify the correctness of your code. No extensive training should be performed on these machines.
  
  - **Training Servers**: These servers can be booked for time-slots in the range of days (maximum 5 straight days). You can use these machines to launch extensive training sessions and experiments. These machines should always run at maximum computational overload. No proofing should be performed on these machines. If by the end of the reservation, no other user has booked the machine, you can extend your reservation for additional (maximum) 5 days.

- **Docker Policy**: It is mandatory to use a Docker container to run your code to ensure maximum virtualization of the resources.

- **Venv Policy**: No virtual environments are allowed on the servers natively, i.e., conda or python venv. You can use them inside your Docker container.

- **Data Policy**: Do not store any datasets on the server's SSD. Data should only be stored on the HDDs and mounted via volume mappings inside the Docker container.

- **Cordiality and Respect**: Maintain a positive and respectful atmosphere for shared usage.

- **Experiment Continuity**: Avoid interrupting another user’s experiment, even if it is outside the booking schedule. Always communicate via the labrococo Google group if there’s an issue.

- **Conflict Resolution**: In case of a scheduling conflict, attempt to resolve it privately before taking any actions.

Logging In
----------

After a reservation has been made on the calendar, follow these steps to access the server:

1. **Log In**: Connect via SSH using the following command:

   .. code-block:: bash

      ssh guest@<ipServer>

   - **Password**: written inside the LabRoCoCo’s Google Calendar description.

2. **Check GPU Usage**: Use the following commands to check GPU and server load:

   .. code-block:: bash

      nvidia-smi
      htop

3. **Workspace Directory**: Create a workspace directory for your experiments. This directory will then be mounted and mapped by you to your Docker container workspace directory.

   .. code-block:: bash

      mkdir /home/guest/SURNAME


Contacts
--------
- **Professor**: iocchi@diag.uniroma1.it
- **Admins**: suriani@diag.uniroma1.it, argenziano@diag.uniroma1.it