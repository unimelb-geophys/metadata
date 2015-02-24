
Metadata has been updated to be as compatible as possible with waveform data downloaded directly from our servers. 

Unfortunatly, we will still need to correct the 'network' of the waveform data to '01' (it is currently blank). We were unable to change the metadata to have no network code, because the PDCC tool used requires this to create metadata files. 

This can be done simply in a python script. 

	e.g. 
		from obspy import read, read_inventory
		st = read("wave.form.file.in")

		tr0 = st[0]
		tr1 = st[1]
		tr2 = st[2]

		tr0.stats["network"] = "01"
		tr1.stats["network"] = "01"
		tr2.stats["network"] = "01"

		st.write("wave.form.file.out", format="MSEED")


This isn't automated yet, but hopefully will be soon. If doing this however, must be careful not to change the network code of any of the borehole stations, as these are correctly labelled 'UM'.
