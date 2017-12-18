# JSON SELECTOR


	usage: jsonSelector [-h] [-i FILE] [-o FILE] [-a] [-d] [-e] [-l] [-q] [-r]
	                    [-s VALUE] [-S COLUMN VALUE COLUMN VALUE] [-w STR]
	                    column [column ...]
	
	positional arguments:
	  column                columns to be displayed
	
	optional arguments:
	  -h, --help            show this help message and exit
	  -i FILE, --infile FILE
	                        input file
	  -o FILE, --outfile FILE
	                        output file
	  -a, --all             List all columns
	  -d, --describe        List column names and exit
	  -e, --printEmpty      print empty rows
	  -l, --listColumnNames
	                        List column names above rows
	  -q, --quiet           suppress warnings
	  -r, --removeDuplicates
	                        Remove duplicate rows while printing
	  -s VALUE, --search VALUE
	                        Show only rows with this value
	  -S COLUMN VALUE COLUMN VALUE, --Search COLUMN VALUE COLUMN VALUE
	                        Show only rows with given value in given column
	  -w STR, --dataWrapper STR
	                        Json Data name default: data

Ex.
	
	cat << EOF > json.json
	{ "data":[
		{
		"id":23,
		"name":"John",
		"LastName":"Smith",
		"Time":"Today"
		},{
		"id":24,
		"name":"Bill",
		"LastName":"Smith",
		"Time":""
		},{
		"id":25,
		"Name":"Sarah",
		"LastName":"Sammy",
		"Time":"Noon"
		}
	]
	}
	EOF
	
	
	jsonSelector -i json.json -d
	id
	Name
	LastNme
	Time
	
	jsonSelector -i json.json Time
	Today
	Noon
	
	jsonSelector -i json.json -o json.txt id
	cat json.txt
	23
	24
	25
	
	jsonSelector -i json.json -a
	23 John Smith Today
	24 Bill Smith
	25 Sarah Sammy Noon
	
	jsonSelector -i json.json -a -l
	id Name LastName Time
	23 John Smith Today
	24 Bill Smith
	25 Sarah Sammy Noon

	jsonSelector -i json.json -l Name
	Name
	John
	Bill
	Sarah
	
	jsonSelector -i json.json -r LastName
	Smith
	Sammy
	
	jsonSelector -i json.json -e Time
	Today
	
	Noon

	jsonSelector -i json.json id -s Noon
	25
	
	jsonSelector -i json.json id -S Name Bill
	24
	
	
	
