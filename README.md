A Formal Framework for Security Testing of
Automotive Over-The-Air Update Systems


Prerequisites:

The code and tests were used on a windows 10 machine with python 2.7
and FDR4 installed.



Attack files:
	Each attack file contains a NewTC.cspm, Report.txt and TCX.cspm
	files. NewTC.cspm is edited by the Python script (TCGen) to
	include new testcase as they are created and then sent to FDR4.
	Report.txt shows how many lines each testcase has and how long
	it took to generate the testcase. TCX.cspm files will start at
	TC1 and increment depending on the number of tests conducted.

- Block
	This contains the files used and generated in the block attack,
	1 test case file.
- Eaves
	This contains the files used and generated in the eavesdropping
	attack, 18 test case files.
- Edit
	This contains the files used and generated in the edit attack
	with keys, 2 test case files.
- EditWO
	This contains the files used and generated in the edit attack
	without keys, 0 test case file.
- Freeze
	This contains the files used and generated in the freeze
	attack, 0 test case file.
- Spoof
	This contains the files used and generated in the spoof attack,
	2 test case files.



Python:

- TCGen
	The python file will need the correct placement of the attack
	files to function. This Python code will also need to be run in
	2.7, not 3.8. Running this script will start the process of
	testing all the attacks against the current model. Towards the
	end of the process, you may find a significant slowdown. This
	can be mitigated by stopping the process, commenting out the
	completed tests and then running the script again. If running
	this test multiple times the attack files should be empty, if a
	partial test was done and needs to be repeated remove or delete
	any documents in the attack files.



Verification:
	The verification files are used to verify the authenticity of
	the metadata sent from the director and the image repository.

- Root_Full_Verification.cspm
	This is used by the primary ECU to verify the root metadata.

- Snapshot_Full_Verification.cspm
	This is used by the primary ECU to verify the snapshot
	metadata.

- Targets_Full_Verification.cspm
	This is used by the primary ECU to verify the targets
	metadata.

- Targets_P_Verification.cspm
	This is used by the secondary ECU to do a partial verification
	on the targets metadata.
	
- Timestamp_Full_verification.cspm
	This is used by the primary ECU to verify the timestamp
	metadata.



Components:

- Server.cspm
	The server has all of the metadata that is held within the
	server, as well as all the processes taken out by the director
	and the image repository.

- Uptane_model.cspm
	This file contains all of the building blocks the other scripts
	are based on, such as defining all the individual processes. It
	also contains the network and the data storage.

- Vehicle.cspm
	The vehicle defines the metadata that is used, it also contains
	all the processes of the primary and secondary ECUs.



Other:

- Attacker.cspm
	This contains all of the attackers and their integration into
	the overall Uptane model, as well as the assertions.

- UptaneFullModel.cspm
	This contains the integrated attacks into the model.
