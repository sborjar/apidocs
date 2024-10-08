# API DOCS

Fecha: 2024-09

> En todos los casos a menos que se especifique se toman los datos como username, email del token y se determina el tenantid en la base para las operaciones

# Lista status con relacion a las llamadas activas campaign y agent

`En ADMIN => NO SE USA | No se utiliza |  Ruta comentada desde la base`

```php
$app->get('/astcalls', \App\Controllers\CallsController::class . ':listall')->setName('astcalls');
```
```json
[
	{
		"statusid": 919943,
		"callId": "ip-172-30-3-185.ec2.internal-1666630848.7267",
		"callerId": "4707567517",
		"status": "CONNECT",
		"timestamp": "2022-10-24 12:00:47",
		"queue": "",
		"position": "",
		"originalPosition": "",
		"holdtime": "",
		"keyPressed": "",
		"callduration": "0",
		"agentid": "442",
		"lineNo": "0",
		"extension": "",
		"leadid": "1128138",
		"callsid": "9679488",
		"camp_id": "252",
		"server_name": "172.30.3.185",
		"server_ip": "172.30.3.185",
		"hangup": "0",
		"call": {
			"callid": 9679488,
			"calldate": "2022-10-24 12:00:14",
			"leadid": "1128138",
			"callresult": "10",
			"agentdisp": "0",
			"agentid": "442",
			"origagentid": "0",
			"linkedcall": "0",
			"calltype": "C",
			"revenue": "0.00",
			"dnis": "4707567517",
			"phone": "7703392945",
			"camp_id": "252",
			"poolid": "361",
			"processed": "0",
			"callduration": "0",
			"billsec": "0",
			"holdtime": "0",
			"position": "0",
			"outbchannel": "",
			"cuniqueid": "ip-172-30-3-185.ec2.internal-1666630848.7267",
			"transituniqueid": "ip-172-30-11-207.ec2.internal-1666630814.6420",
			"userfield": "",
			"amd": "no",
			"amdreason": "",
		
		},
		"agent": {
			"agentid": 442,
			"onHold": "0",
			"agent_code": "kg6712",
			"name": "Kimberly Gilbert",
			"autologoff": "15",
			"ackcall": "no",
			"wrapuptime": "0",
			"musiconhold": "agents",
			"updatecdr": "yes",
			"group": "",
			"recordagentcalls": "",
			"recordformat": "wav",
			"createlink": "yes",
			"urlprefix": "",
			"savecallsin": "",
			"custom_beep": "beep",
			"status": "LOGOFF",
			"statustime1": "2021-12-15 15:38:49",
			"tenantid": "98",
		
		},
		"campaign": {
			"camp_id": 252,
			"camp_name": "comfort_control_outbound",
			"trunkID": "3",
			"camp_channels": "0",
			"ivrid": "0",
			"amdivrid": "0",
			"phoneID": "0",
			"tenantid": "98",
			"groupid": "78",
			"camp_description": "",
			"active": "y",
			"started": "00:00:00",
			"camp_type": "CL",
			"ratio": "1:1",
			"status": "0",
			"inbound_number": "_cmp252$$",
			"queue_name": "q984e1f46f91329602b8",
			"maxretrys": "100",
			"waittime": "70",
			"callerid": "4707567517",
			"busyretrytime": "3000",
			"amdretrytime": "172800",
			"startdialing": "00:00:00",
		}
	},
]
```
# Devuelve los agentes activos 

>`ADMIN`. se utiliza en dos lugares para obtener la lista de agentes activos para el chat y para el `Screen Active Agents` los lista y pone en una tabla.

```php
$app->get('/activeagents[/{campid}]', \App\Controllers\AgentController::class . ':getAgentsActive');
```
```json
[
	{
		"agentid": "433",
		"agent_code": "je5611",
		"name": "Jeff Edwards",
		"status": "TALKING",
		"sessionstart": "2022-10-24 08:30:53",
		"timenow": "2022-10-24 10:12:44"
	},
	{
		"agentid": "440",
		"agent_code": "ml6563",
		"name": "Meghan Lawrence",
		"status": "BREAK",
		"sessionstart": "2022-10-24 09:00:40",
		"timenow": "2022-10-24 10:12:44"
	},
]
```
# AREACODES 

Devuelve los areas codes	

`En ADMIN => NO SE USA | No se utiliza |  Ruta comentada desde la base`

```php
$app->get('/areacodes', \App\Controllers\AreacodeController::class . ':listall')->setName('areacodes');	
```
```json
[
	{
		"prefixid": 1,
		"prefix": "201",
		"timeid": "67",
		"stateid": "37",
		"prefixdesc": "",
		"state": {
			"stateid": 37,
			"state_abr": "NJ",
			"state_name": "New Jersey",
			"dls": "1"
		},
		"time_zone": null
	},
	{
		"prefixid": 2,
		"prefix": "202",
		"timeid": "67",
		"stateid": "9",
		"prefixdesc": "",
		"state": {
			"stateid": 9,
			"state_abr": "DC",
			"state_name": "District of Columbia",
			"dls": "1"
		},
		"time_zone": null
	}, 
]	
```
	
Devuelve un area code por su id

`En ADMIN => NO SE USA | No se utiliza |  Ruta comentada desde la base`
```php
$app->get('/areacode/{id}', \App\Controllers\AreacodeController::class . ':getPrefix');
```
```json
[
	{
		"prefixid": 1,
		"prefix": "201",
		"timeid": "67",
		"stateid": "37",
		"prefixdesc": "",
		"state": {
			"stateid": 37,
			"state_abr": "NJ",
			"state_name": "New Jersey",
			"dls": "1"
		},
		"time_zone": null
	}
]
```

Modifica un area code

`En ADMIN => NO SE USA | No se utiliza |  Ruta comentada desde la base`
```php
$app->post('/areacode', \App\Controllers\AreacodeController::class . ':modifyAreacode');
$app->put('/areacode', \App\Controllers\AreacodeController::class . ':modifyAreacode');
```
```php
data: {
	prefixid: $('#prefixid').val(), 
	prefix:  $('#prefix').val(), 
	stateid: $('#stateid').val(),
	timeid: $('#timeid').val(), 
	prefixdesc: $('#prefixdesc').val()
},
```

Borra un area code

`En ADMIN => NO SE USA | No se utiliza |  Ruta comentada desde la base`

```php
$app->delete('/areacode/{id}', \App\Controllers\AreacodeController::class . ':deleteAreacode');
```

# AUDIT 
Recupera un registro de la tabla audit por su id

`En ADMIN => NO SE USA | No se utiliza |  Ruta comentada desde la base`

```php
$app->get('/audit/{id}', \App\Controllers\AuditTrailController::class . ':getAudit');
```
```json
{
	"auditid": 2,
	"ipaddr": "172.30.1.107",
	"userid": "2",
	"function": "modifyUser",
	"object": "App\\Controllers\\UserController",
	"action": "PUT",
	"route": "\/api\/public\/user",
	"initialJson": "{\"userid\":6,\"username\":\"agent\",\"language\":\"en\",\"fullname\":\"Agent\",\"pass\":\"*6BB4837EB74329105EE4568DDA7DC67ED2CA2AD9\",\"accountcode\":\"\",\"context\":\"internal\",\"callback\":\"\",\"dialout\":\"\",\"serveremail\":\"\",\"exitcontext\":\"\",\"ipaddr\":\"\",\"port\":\"5060\",\"regseconds\":\"3600\",\"canreinvite\":\"N\",\"nat\":\"force_rport,comedia\",\"amaflags\":\"default\",\"defaultip\":\"\",\"host\":\"dynamic\",\"callerid\":\"0\",\"no_page\":\"1\",\"utimeout\":\"0\",\"email\":\"cripito.sd@gmail.com\",\"usertype\":\"27\",\"db\":\"\",\"logged\":\"n\",\"stamp\":\"2021-04-21 23:56:07\",\"clientaccess\":\"0\",\"tenantid\":\"25\",\"maxchannels\":\"200\",\"hashed\":\"$2y$10$an8sk6Xv\\\/lSfrXUUZNHxue.wC1YKu8Y5YHa97xDdYx2wTEk0JFkHa\",\"created_at\":\"2019-12-04T10:38:39.000000Z\",\"updated_at\":\"2021-04-21T23:56:07.000000Z\",\"handlingSystem\":\"general\",\"deleted_at\":null,\"directrtpsetup\":\"yes\",\"tlscertfile\":\"\",\"media_use_received_transport\":\"yes\",\"regserver\":\"\",\"lastms\":\"0\",\"defaultuser\":\"\",\"useragent\":\"\",\"callbackextension\":\"\",\"avpf\":\"no\",\"icesupport\":\"no\",\"encryption\":\"no\",\"transport\":\"udp}}",
	"finalJson": "{\"userid\":6,\"username\":\"agent\",\"language\":\"en\",\"fullname\":\"Agent\",\"pass\":\"*6BB4837EB74329105EE4568DDA7DC67ED2CA2AD9\",\"accountcode\":\"\",\"context\":\"internal\",\"callback\":\"\",\"dialout\":\"\",\"serveremail\":\"\",\"exitcontext\":\"\",\"ipaddr\":\"\",\"port\":\"5060\",\"regseconds\":\"3600\",\"canreinvite\":\"N\",\"nat\":\"force_rport,comedia\",\"amaflags\":\"default\",\"defaultip\":\"\",\"host\":\"dynamic\",\"callerid\":\"0\",\"no_page\":\"1\",\"utimeout\":\"0\",\"email\":\"cripito.sd@gmail.com\",\"usertype\":\"27\",\"db\":\"\",\"logged\":\"n\",\"stamp\":\"2021-05-03 22:18:38\",\"clientaccess\":\"0\",\"tenantid\":\"25\",\"maxchannels\":\"200\",\"hashed\":\"$2y$10$an8sk6Xv\\\/lSfrXUUZNHxue.wC1YKu8Y5YHa97xDdYx2wTEk0JFkHa\",\"created_at\":\"2019-12-04T10:38:}}",
	"can_diff": "1",
	"issues": "",
	"created_at": "2021-05-03T22:18:38.000000Z",
	"updated_at": "2021-05-03T22:18:38.000000Z"
}
```

Agrega y/o modifica un audit

`En ADMIN => NO SE USA | No se utiliza |  Ruta comentada desde la base`

```php
$app->post('/audit', \App\Controllers\AuditTrailController::class . ':modifyAudit');
$app->put('/audit/{id}', \App\Controllers\AuditTrailController::class . ':modifyAudit');
```
```js
data = {
	route: '{{auth.api_url}}' + what + 'campaign/' + cmpID,
	action: 'PUT',
	object: 'CampaignController',
	function: what + "Campaign",
	userid: '{{ auth.user.userid }}',
	ipaddr: '{{ ipaddr }}',
	initialJson: JSON.stringify(initialJson),
	finalJson: JSON.stringify(finalJson),
	can_diff: 0,
	issues: ''
  };
```

# Black Listed 

Recupera registros blacklisted

`En ADMIN => NO SE USA | No se utiliza |  Ruta comentada desde la base`

```php
$app->get('/blackslisted', \App\Controllers\BlacklistedController::class . ':blacklistedListAll');
$app->get('/blacklisted/{id}', \App\Controllers\BlacklistedController::class . ':getBlacklisted');
```
TABLA VACIA

Modifica un blacklisted o lo elimina
```php
$app->post('/blacklisted[/{id}]', \App\Controllers\BlacklistedController::class . ':modifyBlacklisted');
$app->put('/blacklisted[/{id}]', \App\Controllers\BlacklistedController::class . ':modifyBlacklisted');
$app->delete('/blacklisted/{id}', \App\Controllers\BlacklistedController::class . ':deleteBlacklisted');
```
```js
var data = {
	"tenantid": parseInt( $("#tenantid").val() ),
	"phonenumber": $("#phonenumber").val(),
};
```


Upload un file con registros para blacklisted

`En ADMIN => NO SE USA | No se utiliza |  Ruta comentada desde la base`

```php
$app->post('/blacklistedupload', \App\Controllers\BlacklistedController::class . ':importBlacklisted');
```
formato:
```
phonenumber,tenantid
32342424,138
```

# LEAD MANAGEMENT 

Recupera un lead por su id, todos los campos de la tabla dialer_leads y su relacion con pool y file template 

`En ADMIN => ` En listado de CALL SEARCH (Serach by Call), en la columna `lead` se da click sobre el boton de la celda del registro de llamada y se despliega un popup con la informacion del lead para modificarla.

```php
$app->get('/lead/{id}', \App\Controllers\LeadController::class . ':leadRead');
```
```json
{
	"lead_id": "25849016",
	"lead_fname": "JULIA",
	"lead_mname": "",
	"lead_lname": "NICKELS",
	"lead_phone": "3177536698",
	"lead_email": "",
	"lead_address": "9105 Tansel Ct",
	"lastupdate": "2024-06-14 16:03:25",
	"lastcallresult": "0",
	"trynumbers": "6",
	"lead_company": "",
	"lead_apto": "",
	"lead_city": "Indianapolis",
	"lead_state": "IN",
	"lead_zip": "46234",
	"lead_description": "",
	"lead_website": "",
	"lead_title": "",
	"callnotes": "",
	"lead_notes": "",
	"nexttry": "-1",
	"manualgen": "n",
	"custom": "IX352",
	"custom1": "IX352-R",
	"custom2": "1",
	"custom3": "sadie@midwestcashoffer.com",
	
	"custom14": "http:\/\/www.midwestcashoffer.com",
	"private": "n",
	"agentid": "5649",
	"poolid": "1647",
	"allow_inbound": "y",
	"lead_phone1": "3172913991",
	"lead_phone2": "3174385812",
	"lead_phone3": "",
	"lead_phone4": "",
	"lead_phone5": "",
	"cdncid": "0",
	"inlinecallid": "7652095159",
	"noavailable": "n",
	"syscallresult": "11",
	"reccalled": "7",
	"prefix": "317",
	"seed": "",
	"priority": "10",
	"lead_import_status": "",
	"fcalldata": "",
	"lead_status": "Q",
	"lead_type": "C",
	"lead_nocontact": "n",
	"lead_besthr": "",
	"camp_id": "433",
	"privatecallbackset": "2024-01-08 17:50:12",
	"privatecallbackcall": "2024-01-08 17:50:12",
	"recordingidname": "",
	"primaryid": "",
	"party": "",
	"gender": "",
	"age": "",
	"tenantid": "139",
	"conferencenumber": "",
	"quotaid": "0",
	"resultid": "0",
	"lead_fullname": "JULIA  NICKELS",
	"permav": "",
	"support": "",
	"congdist": "",
	"statesenatedist": "",
	"statehousedist": "",
	"city": "",
	"polldesc1": "",
	"polldesc2": "",
	"polladdress1": "",
	"q1": "",
	"q2": "",
	"q3": "",
	"q4": "",
	"q5": "",
	"q6": "",
	
	"q49": "",
	"q50": "",
	"exported": "0",
	"pdisync": "0",
	"exported_date": "0000-00-00 00:00:00",
	"phone_type": "",
	"ts_projectid": "",
	"revenue": "0.00",
	"stateid": "0",
	"timeid": "96",
	"lastreset": "2024-05-28 11:41:41",
	"lastcalled": "2024-06-14 11:02:31",
	"NAME": "",
	"ZZUNIQUESN": "",
	"ZZUNIQUELS": "",
	"PROJECTID": "18",
	"RID": "0",
	"SERVERID": "0",
	"REFKEY": "",
	"PFROM": "",
	"smsnumber": "",
	"qad": "0",
	"qcresult": "0",
	"uuidfield": "",
	"myuniqueid": "0",
	"vanid": "0",
	"phoneid": "0",
	"canvassfilerequestid": "0",
	"surveyid": "0",
	"fdeleted": "0",
	"exported_os": "0",
	"pool": {
		"poolid": "1647",
		"pooluploadname": "",
		"poolname": "IX352_CE.csv",
		"poolfile": "IX352_CE.csv",
		"pooldate": "2024-01-08 17:45:47",
		"firstline": "List,First Name,Last Name,Property Address,Property City,Property State,Property Zip,Phone 1 Number,Phone 2 Number,Phone 3 Number,Phone 4 Number,Phone 5 Number,Phone 6 Number,Email 1 Address",
		"totalrecords": "54925",
		"dedupopts": "f",
		"errors": "0",
		"dbPool": "0",
		"odbc": "",
		"config": "",
		"prefixlen": "3",
		"randomize": "y",
		"listnumbers": "23,1,3,6,12,13,14,4,50,51,52,53,-1,5",
		"listline": "custom1,lead_fname,lead_lname,lead_address,lead_city,lead_state,lead_zip,lead_phone,lead_phone1,lead_phone2,lead_phone3,lead_phone4,lead_email",
		"sqlstring": null,
		"camp_id": "433",
		"FieldCond": "",
		"OperCond": "",
		"ValueCond": "",
		"CleanOld": "0",
		"tenantid": "139",
		"templateid": "942",
		"imported": "1",
		"startstop": "1",
		"created_at": "2024-01-08 17:45:47",
		"updated_at": "2024-06-13 16:56:11",
		"deleted_at": null,
		"export_fields": "",
		"export_where": "",
		"integration_type": "0",
		"savedlist": "0",
		"mark_final_crc": "0",
		"show_alert": "31",
		"dbsync": "0",
		"binarycondition": "",
		"archived": "0",
		"archived_time": null,
		"file_template": {
			"id": 942,
			"tenantid": "139",
			"template_name": "IX352_CE.csv-template",
			"file_header": "List,First Name,Last Name,Property Address,Property City,Property State,Property Zip,Phone 1 Number,Phone 2 Number,Phone 3 Number,Phone 4 Number,Phone 5 Number,Phone 6 Number,Email 1 Address",
			"listline": "custom1,lead_fname,lead_lname,lead_address,lead_city,lead_state,lead_zip,lead_phone,lead_phone1,lead_phone2,lead_phone3,lead_phone4,lead_email",
			"listnumbers": "23,1,3,6,12,13,14,4,50,51,52,53,-1,5",
			"created_at": "2024-01-08T17:45:39.000000Z",
			"updated_at": "2024-01-08T17:49:05.000000Z",
			"deleted_at": null,
			"fields": [
				{
					"id": 13488,
					"field_name": "List",
					"field_source": "List",
					"field_destination": "custom1",
					"file_template": "942",
					"created_at": "2024-01-08T17:45:39.000000Z",
					"updated_at": "2024-01-08T17:49:05.000000Z",
					"deleted_at": null
				},
				{
					"id": 13489,
					"field_name": "First Name",
					"field_source": "First Name",
					"field_destination": "lead_fname",
					"file_template": "942",
					"created_at": "2024-01-08T17:45:39.000000Z",
					"updated_at": "2024-01-08T17:49:05.000000Z",
					"deleted_at": null
				},
				{
					"id": 13490,
					"field_name": "Last Name",
					"field_source": "Last Name",
					"field_destination": "lead_lname",
					"file_template": "942",
					"created_at": "2024-01-08T17:45:39.000000Z",
					"updated_at": "2024-01-08T17:49:05.000000Z",
					"deleted_at": null
				},
				
			]
		}
	}
}
```

Modifica un lead desde un formulario

`En ADMIN => ` del popup presentado al momento de guardar se envia a esta ruta los datos siguientes:
```js
{
    lead_fname:$("div#leadMod #lead_fname").val(),
    lead_mname:$("div#leadMod #lead_mname").val(),
    lead_lname:$("div#leadMod #lead_lname").val(),
    lead_address:$("div#leadMod #lead_address").val(),
    lead_city:$("div#leadMod #city").val(),
    lead_state:$("div#leadMod #lead_state").val(),
    lead_zip:$("div#leadMod #lead_zip").val(),
    custom:$("div#leadMod #custom").val(),
    custom1:$("div#leadMod #custom1").val(),
    custom2:$("div#leadMod #custom2").val(),
    custom3:$("div#leadMod #custom3").val(),
    custom4:$("div#leadMod #custom4").val(),
    custom5:$("div#leadMod #custom5").val(),
    custom6:$("div#leadMod #custom6").val(),
    custom7:$("div#leadMod #custom7").val(),
    custom8:$("div#leadMod #custom8").val(),
    custom9:$("div#leadMod #custom9").val(),
    custom10:$("div#leadMod #custom10").val(),
    custom11:$("div#leadMod #custom11").val(),

    lead_notes:$("div#leadMod #lead_notes").val(),
    revenue:$("div#leadMod #revenue").val(),
}
```

```php
$app->put('/lead/{id}', \App\Controllers\LeadController::class . ':leadSave');
```
```json
{
    "lead_fname": "Joseph",
    "lead_mname": "",
    "lead_lname": "Doll",
    "lead_address": "362 E Arch St",
    "lead_city": "Indianapolis",
    "lead_state": "IN",
    "lead_zip": "46202",
    "custom": "3035",
    "custom1": "",
    "custom2": "1",
    "custom3": "amanda@midwestcashoffer.com",
    "custom4": "00D4x000002zP5R",
    "custom5": "3",
    "custom6": "2.5",
    "custom7": "No Basement",
    "custom8": "2C Detached",
    "custom9": "Divorce",
    "custom10": "Cold Call",
    "custom11": "NEW",
    "lead_notes": "have a stroke recently TEST",
    "revenue": "0.00"
}
```

Devuelve las columnas de la tabla dialer_leads (filtradas)

`En ADMIN =>` Se utiliza para obtener un listado de columnas para el `wizard de new campaign` , `campaign edit`, a fin de que en CALL DATA se pueda seleccionar y poner los campos que desen que aparezca en CALL INFO en el agente.

```php
$app->get('/lead_columns', \App\Controllers\LeadController::class . ':leadColumns');
```
```json
[
	"lead_fname",
	"lead_mname",
	"lead_lname",
	"lead_phone",
	"lead_email",
	"lead_address",
	"lead_company",
	"lead_apto",
	"lead_city",
	"lead_state",
	"lead_zip",
	"lead_description",
	"lead_website",
	"lead_title",
	"callnotes",
	"lead_notes",
	"custom",
	"custom1",
	"custom2",
	"custom3",
	"custom4",
	"custom5",
	"custom6",
	"custom7",
	"custom8",
	"custom9",
	"custom10",
	"custom11",
	"custom12",
	"custom13",
	"custom14",
	"custom15",
	"custom16",
	"custom17",
	"custom18",
	"custom19",
	"custom20",
	"lead_phone1",
	"lead_phone2",
	"lead_phone3",
	"lead_phone4",
	"lead_phone5",
	"primaryid",
	"party",
	"gender",
	"age",
	"lead_fullname",
	"permav",
	"support",
	"congdist",
	"statesenatedist",
	"statehousedist",
	"city",
	"polldesc1",
	"polldesc2",
	"polladdress1",
	"q1",
	"q2",
	"q3",
	"q4",
	"q5",
	"q6",
	"q7",
	
	"q50",
	"lastcalled",
	"NAME",
	"ZZUNIQUESN",
	"ZZUNIQUELS",
	"PROJECTID",
	"RID",
	"SERVERID",
	"REFKEY",
	"PFROM",
	"smsnumber",
	"qad",
	"qcresult",
	"uuidfield",
	"myuniqueid",
	"vanid",
	"phoneid",
	"canvassfilerequestid",
	"surveyid",
	"fdeleted"
]
```

# CALLTIME 

Creo que es antigua
devuelve uno mas registros de la tabla calltime

`En ADMIN => NO SE USA`.

```php
$app->get('/calltimes', \App\Controllers\CallsController::class . ':getCallTimes');
$app->get('/calltime/{id}', \App\Controllers\CallsController::class . ':getCallTime');
```
```json
[
	{
		"calltimeid": 99,
		"name": "default",
		"tenantid": "-1",
		"defaultstart": "6:00",
		"defaultstop": "21:00",
		"defaultactive": "y",
		"sundaystart": "0:00",
		"sundaystop": "0:00",
		"sundayactive": "y",
		"mondaystart": "0:00",
		"mondaystop": "0:00",
		"mondayactive": "y",
		"tuesdaystart": "0:00",
		"tuesdaystop": "0:00",
		"tuesdayactive": "y",
		"wednesdaystart": "0:00",
		"wednesdaystop": "0:00",
		"wednesdayactive": "y",
		"thursdaystart": "0:00",
		"thursdaystop": "0:00",
		"thursdayactive": "y",
		"fridaystart": "0:00",
		"fridaystop": "0:00",
		"fridayactive": "y",
		"saturdaystart": "0:00",
		"saturdaystop": "0:00",
		"saturdayactive": "y"
	}
]
```


Modifica registros de la tabla calltime

`En ADMIN => NO SE USA`.

```php
$app->put('/calltime/{id}', \App\Controllers\CallsController::class . ':callTimeModify');
$app->post('/calltime/{id}', \App\Controllers\CallsController::class . ':callTimeModify');
```
```js
param.name = $("#name").val();
    param.defaultstart = $("#defaultstart").val();
    param.defaultstop = $("#defaultstop").val();
    param.defaultactive = $('#defaultactive').is(':checked') ? 'y' : 'n';
    param.sundaystart = $("#sundaystart").val();
    param.sundaystop = $("#sundaystop").val();
    param.sundayactive = $('#sundayactive').is(':checked') ? 'y' : 'n';
    param.mondaystart = $("#mondaystart").val();
    param.mondaystop = $("#mondaystop").val();
    param.mondayactive = $('#mondayactive').is(':checked') ? 'y' : 'n';
    param.tuesdaystart = $("#tuesdaystart").val();
    param.tuesdaystop = $("#tuesdaystop").val();
    param.tuesdayactive = $('#tuesdayactive').is(':checked') ? 'y' : 'n';
    param.wednesdaystart = $("#wednesdaystart").val();
    param.wednesdaystop = $("#wednesdaystop").val();
    param.wednesdayactive = $('#wednesdayactive').is(':checked') ? 'y' : 'n';
    param.thursdaystart = $("#thursdaystart").val();
    param.thursdaystop = $("#thursdaystop").val();
    param.thursdayactive = $('#thursdayactive').is(':checked') ? 'y' : 'n';
    param.fridaystart = $("#fridaystart").val();
    param.fridaystop = $("#fridaystop").val();
    param.fridayactive = $('#fridayactive').is(':checked') ? 'y' : 'n';
    param.saturdaystart = $("#saturdaystart").val();
    param.saturdaystop = $("#saturdaystop").val();
    param.saturdayactive = $('#saturdayactive').is(':checked') ? 'y' : 'n';
    param.tenantid = {{ auth.user.tenantid }};
```

Elimina un registro de calltime con su id

`En ADMIN => NO SE USA`.

```php
$app->delete('/calltime/{id}', \App\Controllers\CallsController::class . ':callTimeDelete');
```

# TENANT 

Devuelve todos los tenants paginado

`En ADMIN => NO SE USA` Porque lo toma desde los models del admin 

```php
$app->get('/tenants[/p/{p}/f/{f}/o/{o}/i/{i}]', \App\Controllers\TenantController::class . ':listall');
```
En este caso no hay normalizacion de la respuesta
```json
[
	{
		"tenantid": 25,
		"name": "Default Tenant",
		"phone": "",
		"address": "",
		"username": "admin",
		"tenantpass": "admin",
		"email": "admin@callevo.com",
		"usertype": "36",
		"maxusers": "50",
		"maxagents": "0",
		"maxcamps": "200",
		"tenantchannels": "20",
		"billingtype": "2",
		"account_balance": "0.0000",
		"bill_rate": "0.00000",
		"increments": "6",
		"start": "6",
		"timeused": "3341.0000",
		"authdomain": "172.30.11.94",
		"siplogin": "sip:kamailio.callevo.net:5060",
		"kamailio": "sip:kamailio.callevo.net:5060",
		"parent": "-1",
		"inbound_number": "",
		"trunkID": "3",
		"dbname": "asterisk_realtime",
		"limitexport": "0",
		"exportcampids": "",
		"limitbilling": "0",
		"camp_type": "CL",
		"activate_tenant": "y",
		"sendclickerevents": "0",
		"pushrecordsp": "PushCallData",
		"tenantkey": "eyJjdHkiOiJKV1QiLCJlbmMiOiJBMjU2R0NNIiwiYWxnIjoiUlNBLU9BRVAifQ.axjOMMxsbHwr4JZU956J1NZsbIUj5cZGtqbuEIlrhUtyNRVbY_CXKdM302Xnhro0173aDcY7A0KhIKxZIRgYYCt9usFfjljv_vEIl6VD9NcjR70tYhL4v13LAhou0fNKq2xfdc3BAkXWG1oVt5crWLLTlpY_yFL8v-GJD96Y-g07AunlosWIhmOVN21-vF4HJmv91lz00Tsni10Eg2s05ekMoHgaZyYHUIUmUmC31XnG22t1JAZ0e4yC6UAGj9jS_3BIoXukwb2H1I-yFrMXko_QX-JyhOsEx6_49fFLwcS4A5EBD_j_FRMbEFPOCnBUfrr3-Uy5bXDaICHI164aRA.trpcTT8rjgyB1uTA.U1vhRlNISPUrKMOnbyuX10ovA32EBFminFTS7FdfZFe-MGq7FTl-EiJ-lYmj6yBgJfv3JE9nKd3zZtnR85x55lCJYP4fmiwZFwmg-XTTWkUVamvm3GqvoxJG_cHN7qNb2whglTyd5KtsiTRI_N2otjiV5Zi2ue1LheMtIUtt9I2QLwJsywA9gvhABKEiNCSOVqU-UPVqdBiWfwb8j08jFrdN1NlPIoDnoGKZFQZhMSxY0mLGNsQ9uqbm0pYI0URTey2G3MtEhwGkAUYh2YwakaaCvIavV0cTvktaKChxoduzGfJ1syXTUpH-Hky0Hzg723HuT7Ut5iZpfkKJHxcxM7CaVNUlajguMqaanf6-5kEzkiUDImWG2lUkrkgwvwvBdhiyYwX2fmebd38E6vQOkFijOdCJiH5QQWXRAo2wWDOt7BPU9tR7dxaSAwQqoJSo-Jf5wWcn07HFbjCBGfvxx0kQqLJo-KozCOZCW_tD4Pi4-tJxnEGoTbgSDGJla6rPefYpfGnviWKrc72J_bFsgfu3XHj0wyIfZrqrYo1ijtpN8R8I822-M4THDl6V1FDZ8P9Zrx--2JNFLYn4wyJ59f38iqcjXXCyc7OLYvNN5a63l1fWeplR_t_vxv6-lfsvw4axkgC--JIMDbIYfSiPlIvOypSINqxaB20cagRpaMt6GiZx2nyXKc5Tm2Sjp3DHNztKhEcrCX3eKQbeUComEwsQL4tpRxBNdn6d-vu-JCzsRsHTGOmWTq1kDUD8lrTW0VGski8rKgS6xhUOMOJkpaQqT2ty9Nf3ei0gw13o-L4h3rRo6fiXLwrK4j5Wud9m1cRnfSn6qTi5qBwuLt9Oy3SZxjcDKP-ILHmEh13pZyNwPyd4F0-5-0DRwy69YvodHfW-nzoX1uDwMpZJbobtgB1kdWYEqI_rNO2JppN6vkhsEeB1qRvCRQkHguW-U3lyAT0zeAZbky15_SZJDw3tvCA0uG5kbnxUtWzurB7jDgGnO0j8BiI9WNmCZv6BqIVGW6Kk8f0rcyECMF2wU7RFmh9GVx2lXF2qD-yXekcPr6grrJgckzmiZiOjCNEVl_6xJJQ-0V3ToW0U8FJyct25svNYuXOHi9CYXnS3f5teMW3SmwYlWW62APo5i-Y00hAdbv4EuzFBeVBcCpsiR_FDkIIc9NkwxKqmbaWvWFaCiQW6fZ8tMeJ21e_fGghm1YP_e6PlPTvmiad0x9-EFzkH8ySRpOpfJdWAdbEJeF7RD3Zb6vj-6VtSLL_qRU5ydU71xgjPk6Y.DYnfKfow6xCvTGEMAt8FnA",
		"tenantuid": "00000",
		"usernamebase": "admin",
		"smsid": "",
		"leadtype": "r",
		"dburl": "https:\/\/apidev.callevo.net\/api\/public",
		"scrub_system": "0",
		"scrub_key": "",
		"lifeortest": "t",
		"internalcrm": "n",
		"leadurl": "",
		"explicitfilter": "y",
		"ngp_van_apikey": "eb16cac1-7845-2405-9b00-40c38ef682cf",
		"ngp_van_api_base_url": "https:\/\/api.securevan.com\/v4\/",
		"ngp_van_app_name": "",
		"ngp_van_cache_ttl": "300",
		"ngp_van_export_job_type_id": "8",
		"ngp_van_maximum_list_size": "75000",
		"ngp_van_webhook_base_url": "https:\/\/api.securevan.com\/v4\/",
		"integration_type": "0",
		"userwebhook": "",
		"teamwebhook": "",
		"userteamwebhook": null,
		"selectcmp": "1",
		"timeid": "52",
		"confirm_email": "0",
		"statusagent": "0001|0001|0001|0001|0001",
		"created_at": "2021-10-03 10:30:05",
		"updated_at": "2021-10-14 10:30:20",
		"deleted_at": null,
		"logo": "",
		"logotype": "",
		"usedispopt": "1",
		"usefilteropt": "1",
		"usescheduleopt": "1",
		"usecalldataopt": "1",
		"podio_active": "n",
		"podio_client_id": null,
		"podio_client_secret": null,
		"podio_app_id": null,
		"podio_app_token": null,
		"allowselectiontype": "1",
		"allowlinkedcampaign": "1",
		"callerid_management": "0",
		"areacode": "123-234-345-456-567",
		"defaultcalleridgroup": "0",
		"tenantami": "172.30.11.94",
		"seepredictive": "1",
		"seemessaging": "1",
		"stand_alone_clicker": "1",
		"nodeid": "6",
		"export": "1"
	}
]
```

Devuelve todos tenants

`En ADMIN => ` La lista de tenants se utiliza en el generador de reportes `Report Generator` para determinar que tenant puede verlo y en que tenant puede hacer un testing. Opción puede ser vizualizada por usuarios de tipo **Callevo**.

```php
$app->get('/list_tenants', \App\Controllers\TenantController::class . ':listCTenants');
```
```json
{
	"status": "ok",
	"message": [
		{
			"tenantid": 25,
			"name": "Default Tenant",
			"phone": "",
			"address": "",
			"username": "admin",
			"tenantpass": "admin",
			"email": "admin@callevo.com",
			"usertype": "36",
			"maxusers": "50",
			"maxagents": "0",
			"maxcamps": "200",
			"tenantchannels": "20",
			"billingtype": "2",
			"account_balance": "0.0000",
			"bill_rate": "0.00000",
			"increments": "6",
			"start": "6",
			"timeused": "3341.0000",
			"authdomain": "172.30.11.94",
			"siplogin": "sip:kamailio.callevo.net:5060",
			"kamailio": "sip:kamailio.callevo.net:5060",
			"parent": "-1",
			"inbound_number": "",
			"trunkID": "3",
			"dbname": "asterisk_realtime",
			"limitexport": "0",
			"exportcampids": "",
			"limitbilling": "0",
			"camp_type": "CL",
			"activate_tenant": "y",
			"sendclickerevents": "0",
			"pushrecordsp": "PushCallData",
			"tenantkey": "eyJjdHkiOiJKV1QiLCJlbmMiOiJBMjU2R0NNIiwiYWxnIjoiUlNBLU9BRVAifQ.axjOMMxsbHwr4JZU956J1NZsbIUj5cZGtqbuEIlrhUtyNRVbY_CXKdM302Xnhro0173aDcY7A0KhIKxZIRgYYCt9usFfjljv_vEIl6VD9NcjR70tYhL4v13LAhou0fNKq2xfdc3BAkXWG1oVt5crWLLTlpY_yFL8v-GJD96Y-g07AunlosWIhmOVN21-vF4HJmv91lz00Tsni10Eg2s05ekMoHgaZyYHUIUmUmC31XnG22t1JAZ0e4yC6UAGj9jS_3BIoXukwb2H1I-yFrMXko_QX-JyhOsEx6_49fFLwcS4A5EBD_.",
			"tenantuid": "00000",
			"usernamebase": "admin",
			"smsid": "",
			"leadtype": "r",
			"dburl": "https:\/\/apidev.callevo.net\/api\/public",
			"scrub_system": "0",
			"scrub_key": "",
			"lifeortest": "t",
			"internalcrm": "n",
			"leadurl": "",
			"explicitfilter": "y",
			"ngp_van_apikey": "eb16cac1-7845-2405-9b00-40c38ef682cf",
			"ngp_van_api_base_url": "https:\/\/api.securevan.com\/v4\/",
			"ngp_van_app_name": "",
			"ngp_van_cache_ttl": "300",
			"ngp_van_export_job_type_id": "8",
			"ngp_van_maximum_list_size": "75000",
			"ngp_van_webhook_base_url": "https:\/\/api.securevan.com\/v4\/",
			"integration_type": "0",
			"userwebhook": "",
			"teamwebhook": "",
			"userteamwebhook": null,
			"selectcmp": "1",
			"timeid": "52",
			"confirm_email": "0",
			"statusagent": "0001|0001|0001|0001|0001",
			"created_at": "2021-10-03 10:30:05",
			"updated_at": "2021-10-14 10:30:20",
			"deleted_at": null,
			"logo": "",
			"logotype": "",
			"usedispopt": "1",
			"usefilteropt": "1",
			"usescheduleopt": "1",
			"usecalldataopt": "1",
			"podio_active": "n",
			"podio_client_id": null,
			"podio_client_secret": null,
			"podio_app_id": null,
			"podio_app_token": null,
			"allowselectiontype": "1",
			"allowlinkedcampaign": "1",
			"callerid_management": "0",
			"areacode": "123-234-345-456-567",
			"defaultcalleridgroup": "0",
			"tenantami": "172.30.11.94",
			"seepredictive": "1",
			"seemessaging": "1",
			"stand_alone_clicker": "1",
			"nodeid": "6",
			"export": "1"
		},
.
]
```

Devuelve 1 tenant por su id

`En ADMIN => OPCION NO ES UTILIZADA` porque se lo hace directamente en el admin por medio de los modelos.

```php
$app->get('/tenant/{id}', \App\Controllers\TenantController::class . ':getTenant');
```
```json
[
	{
		"tenantid": 138,
		"name": "JJSC Tenant test",
		"phone": "",
		"address": "",
		"username": "u255003d99d21e651a0a",
		"tenantpass": "s6P7v4K1",
		"email": "jsainz@callevo.com",
		"usertype": "37",
		"maxusers": "50",
		"maxagents": "0",
		"maxcamps": "200",
		"tenantchannels": "20",
		"billingtype": "2",
		"account_balance": "0.0000",
		"bill_rate": "0.00000",
		"increments": "6",
		"start": "6",
		"timeused": "4495.0000",
		"authdomain": "172.30.11.94",
		"siplogin": "sip:kamailio.callevo.net:5060",
		"kamailio": "sip:kamailio.callevo.net:5060",
		"parent": "-1",
		"inbound_number": "",
		"trunkID": "8",
		"dbname": "asterisk_realtime",
		"limitexport": "0",
		"exportcampids": "",
		"limitbilling": "0",
		"camp_type": "CL",
		"activate_tenant": "y",
		"sendclickerevents": "1",
		"pushrecordsp": "PushCallData",
		"tenantkey": "eyJjdHkiOiJKV1QiLCJlbmMiOiJBMjU2R0NNIiwiYWxnIjoiUlNBLU9BRVAifQ.nFqsMZW3cbWjXejbocJBRC9mwe7LICg4UVOjHy_SkXsruUTiDNyc1D3zFFsI5bSWDd9fy4-Ij7c-7vGkzvKMBE3L6g3nTkDwDCiQPQMOYrLgQ33bqnuxWR6wjg1jO9-ZRKcm1UG1GG__ENXrvA3nE5ILjMBePReGNmUbHCkmh0RCItBgaEInD23iPfHj4mCcaO8sjRCLSSUMf2iBlDMwTqNKWhZVXlgXGmq720rpORiIw9v6QRdJxyZJyIsbFCJ6S3ZRHgxFR2f5ls0zMKZWvCIapqK792Ycg1S8Oh7dCFVME61RVTzpsJZ6XOsz47bgEePLT-bYhXDzqVnRRVhtAA.k3BCkwGk08YWMh-q.fc_JP1-OJWXBA-_166fQmO1NWCA5zrnP7t0zBC87cjrwqnrgc_xg-RlVv9Z3P_1pytIp5uGiXuB94ogL1bUxo0wMXTqHuejZDIU0RCPPJ4dy299JlSvwhYCyhp50nAIBY29SluGiT6lQ8saIyVk1wZogLe-DDspdvAn0rABeZY3Nck8vKABXH1cQHx3a12wpEoFLxREW6hI4tx2lAljU_9RPck-FGeqJUef5n-FAOZVf79HBoLXR1vgyrECoS36diwmEg_vxCJ_hPpcQb4hdU2xSiEMMBNlKSwn2l-A5s13vLTbaYYANZSqLvPASgReUQe7Z9gvzSvv3fosPZahfH0XeYmENUhx87MIEGfn-FWq6eLixtzs0i7ZFJWoXmx2r5hteWp6ilC_F-HuOd2ayHaSkx7KvY3bFzZGNr3wy07npMWZAK5yFUDN_4s6oPAsHwnfPx-DPM-LEj7IRbS4-eksx4IumnSaGwfYzRWGjtfnFkJD1SroThemO1RDav2qjrcWtZnrJd0J0J3WMILe0OuZk2GoAoYEPfC8m3juj5ZmcWVCDevzTIFOOiTMDJWsNSfGbAE94yTR4fRvrip-fEtOqoZAdnCr0PxZ69GPU-y8V6M4ej2Eq7L-aPK9iT5IH3A_K6bj5bQIrsYqY78RrUDkEui-6ZyN-069sK1lPkWNkKW7oioHwuEMRJqmyN1AtDUrTzuybiYz2OPQIXTmyuEbC0Pzs0KIYB4rFlgxNWD_w_VoK1apB2-4YczZT4aobcLa5pUWucdvjud3zCIUSbzt6Lrxw2pE8AD8KN2fjEsxcacVPijednP5EAN4fNg9--LRUP1crd_BGT7jgoLrA8X-pL02p6vZl8YjVPvpmbDYEmm4VuwVg29ai45jS2i0W9uercsXR_UzfUMMGroej8WT-HXAosJwRWIxzmDq-YjtSkOfns5t-oXvh84X_F3g4XiaoeVTi0FDLweIdxajBtUl_LATDHrRHTSewW_cUGDP9TqShO4ra5S5H6-tLZY9qa2vOy7uZxQHGzx_a7pXZ__cVnQ82NFID64KVtZYbBba3Mn70oOsD4hYzVJBhIcEJBNF3G4gD39M3B8-sp_mDJ8z2kBG7H9kitIGgavl9cmf6Y2r8Uh5L4Zeko4R16hU-h9tcWe45NcPs1bpPAZpw-6ofGhAebpnuJFR8bHeUvj9APXj6ix8LsRzGD16_CTsAXevGWMkM3rp5ZoHac6FXDkTPnVBbRpmavu1L1Ca9oNHcGlbgZyrNzko7lYNBGuq0LMf7L5Lb1czWFF-hrohaIijm6J0Cbt_dfg.7kkYF_E_ZbKgr0l9hbAo2Q",
		"tenantuid": "01040",
		"usernamebase": "u255003d99d21e651a0a",
		"smsid": "",
		"leadtype": "r",
		"dburl": "https:\/\/api.callevo.net\/api\/public",
		"scrub_system": "0",
		"scrub_key": "",
		"internalcrm": "n",
		"leadurl": "",
		"explicitfilter": "y",
		"ngp_van_apikey": "9nwAJOZiZOX2yaNRLvrjgw==",
		"ngp_van_api_base_url": "",
		"ngp_van_app_name": "",
		"ngp_van_cache_ttl": "300",
		"ngp_van_export_job_type_id": "8",
		"ngp_van_maximum_list_size": "75000",
		"ngp_van_webhook_base_url": "https:\/\/app.securevan.com\/v4\/",
		"userwebhook": "",
		"teamwebhook": "",
		"userteamwebhook": "",
		"selectcmp": "1",
		"timeid": "49",
		"confirm_email": "0",
		"statusagent": "0001|0001|0001|0001|0001",
		"created_at": "2022-10-19 14:39:08",
		"updated_at": null,
		"deleted_at": null,
		"logo": "HC1LNM_logo_Image_2021-01-03_at_5.20.50_PM",
		"logotype": "jpeg",
		"usedispopt": "1",
		"usefilteropt": "1",
		"usescheduleopt": "1",
		"usecalldataopt": "1",
		"podio_active": "n",
		"podio_client_id": null,
		"podio_client_secret": null,
		"podio_app_id": null,
		"podio_app_token": null,
		"allowselectiontype": "0",
		"allowlinkedcampaign": "1",
		"callerid_management": "1",
		"areacode": "",
		"defaultcalleridgroup": "0",
		"tenantami": "172.30.11.94",
		"seepredictive": "0",
		"seemessaging": "0",
		"stand_alone_clicker": "1",
		"nodeid": "6",
		"export": "0"
	}
]
```

Modifca o inserta un tenant

`En ADMIN =>` se utiliza en la opcion `Tenant Edit` para guardar los cambios.

```php
$app->put('/tenant/{id}', \App\Controllers\TenantController::class . ':modifyTenant');
$app->post('/tenant', \App\Controllers\TenantController::class . ':modifyTenant');   
```
```json
{
	"tenantid": "25",
	"tenant": {
		"tenantid": 25,
		"name": "Default Tenant",
		"phone": "",
		"address": "",
		"username": "admin",
		"tenantpass": "admin",
		"email": "admin@callevo.com",
		"usertype": "36",
		"maxusers": "50",
		"maxagents": "0",
		"maxcamps": "200",
		"tenantchannels": "20",
		"billingtype": "2",
		"account_balance": "0.0000",
		"bill_rate": "0.00000",
		"increments": "6",
		"start": "6",
		"timeused": "3195.0000",
		"authdomain": "kamailio.callevo.net",
		"siplogin": "sip:kamailio.callevo.net:5060",
		"kamailio": "sip:kamailio.callevo.net:5060",
		"parent": "-1",
		"inbound_number": "",
		"trunkID": "3",
		"dbname": "asterisk_realtime",
		"limitexport": 0,
		"exportcampids": "",
		"limitbilling": 0,
		"camp_type": "CL",
		"activate_tenant": "y",
		"sendclickerevents": "0",
		"pushrecordsp": "PushCallData",
		"tenantkey": "eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCIsImtpZCI6ImJNT1Fia0t1ekNnUmp6OEdwVS1GayJ9.eyJpc3MiOiJodHRwczovL2F1dGguY2FsbGV2by5uZXQvIiwic3ViIjoiVTY3VlNROVViRlZ6N1YxZzUxbVRzZGFRb0xXaGRWdzRAY2xpZW50cyIsImF1ZCI6Imh0dHBzOi8vYXV0aC5jYWxsZXZvLm5ldCIsImlhdCI6MTYyNjczMzU3MSwiZXhwIjoxNjI5MzI1NTcxLCJhenAiOiJVNjdWU1E5VWJGVno3VjFnNTFtVHNkYVFvTFdoZFZ3NCIsInNjb3BlIjoiY3JlYXRlOnVzZXIgcmVhZDp1c2VyIGRlbGV0ZTp1c2VyIHVwZGF0ZTp1c2VyIiwiZ3R5IjoiY2xpZW50LWNyZWRlbnRpYWxzIiwicGVybWlzc2lvbnMiOlsiY3JlYXRlOnVzZXIiLCJyZWFkOnVzZXIiLCJkZWxldGU6dXNlciIsInVwZGF0ZTp1c2VyIl19.iP0ow9XHw13qVbLUZbVM6VEcacDWL_29I4TU8D7HJ0mueJiS0ebqoF2x1pY6G-pNxVaiubLmoRW9G6xAwlKIGLjGxCzZ-ufjkEKel2x2Nenn3fZB2tpcmg_VWiv0KoIJzxfRSTpEk9w_LAob6r92t-C3RlG6prBScpY6H8CWazuF3Eo0DQS3vZE-4EPWcplyImFVKRhH8-fGSaM4DoPD-3YudkvjxNSUKtRuv4Ig04TBNZCOPkgPXhdfs5k98WBtD8fQt3PK_QgQHqtOuUwOL3SNktdov--1lB5xs_TzYHWK6Odmqpo_cM9mnyClVFmYrzA0K5Jr01jT2gVpBkX61A",
		"tenantuid": "00000",
		"usernamebase": "admin",
		"smsid": "",
		"leadtype": "r",
		"dburl": "https://apidev.callevo.net/api/public",
		"scrub_system": "0",
		"scrub_key": "",
		"lifeortest": "t",
		"internalcrm": "n",
		"leadurl": "",
		"explicitfilter": "n",
		"ngp_van_apikey": "",
		"ngp_van_api_base_url": "https://api.securevan.com/v4/",
		"ngp_van_app_name": "",
		"ngp_van_cache_ttl": 300,
		"ngp_van_export_job_type_id": 8,
		"ngp_van_maximum_list_size": 75000,
		"ngp_van_webhook_base_url": "https://api.securevan.com/v4/",
		"integration_type": 0,
		"userwebhook": "",
		"teamwebhook": "",
		"userteamwebhook": "",
		"selectcmp": "1",
		"timeid": "52",
		"confirm_email": 0,
		"statusagent": "0001|0001|0001|0001|0001",
		"created_at": "2021-10-03 10:30:05",
		"updated_at": "2021-10-14 10:30:20",
		"deleted_at": null,
		"logo": "\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u000",
		"logotype": "",
		"usedispopt": "1",
		"usefilteropt": "1",
		"usescheduleopt": "1",
		"usecalldataopt": "1",
		"podio_active": "n",
		"podio_client_id": null,
		"podio_client_secret": null,
		"podio_app_id": null,
		"podio_app_token": null,
		"allowselectiontype": "y",
		"allowlinkedcampaign": "1",
		"callerid_management": 0,
		"areacode": "123-234-345-456-567",
		"defaultcalleridgroup": "0"
	}
}
```
resultado
```php
{ 
	"status": "ok", 
	"message":  $tenantid."|".$userid
}
```
o el error correspondiente


Borra un tenant

`En ADMIN =>` se utiliza en la opción `Tenants` o en el listado de tenants, que al seleccionar un registro y dar click sobre el boton eliminar, y luego de confirmarlo, lo pueda eliminar.

```php
$app->delete('/tenant/{id}', \App\Controllers\TenantController::class . ':deleteTenant');
```
parametro de entrada
```json
{
	"softd" : 0
}
```
#### IMPORTANTE
Si es 0 se elimina fisicamente todo lo relacionado con el tenant, y si es 1 se usan los modelos son soft delete
```php
Pools::where("tenantid", $id)->delete();
PoolStats::where("tenantid", $id)->delete();
CampaignPool::where("tenantid", $id)->delete();
Lead::where("tenantid", $id)->delete();
Call::where("tenantid", $id)->delete();
DncComplain::where("tenantid", $id)->delete();
DncGlobal::where("tenantid", $id)->delete();

QueueTable::where('tenantid', $id)->delete();
FileTemplate::where('tenantid', $id)->delete();
UIProject::where('tenantid', $id)->delete();
LeadFlag::where('tenantid', $id)->delete();

Agent::where('tenantid',$id)->delete();
User::where('tenantid', $id)->delete();
TimeZone::where('tenantid', $id)->delete();
Disposition::where('tenantid', $id)->delete();
Survey::where("tenantid", $id)->delete();
Campaign::where('tenantid', $id)->delete();

Phone::where("tenantid", $id)->delete();
Tenant::where("tenantid", $id)->delete();
```


# STATS 

Estas rutas estan usadas via NATS dsesde el admin

`En ADMIN => NO SE USA se usaba en admin`

```php
$app->get('/projectstats', \App\Controllers\CmpStatsController::class . ':listall')->setName('projectstats');
$app->get('/cmpstats[/{db}]', \App\Controllers\CmpStatsController::class . ':cmpstats')->setName('cmpstats'); <= sacarlas de la db 
$app->get('/cmpstatsqs', \App\Controllers\CmpStatsController::class . ':cmpstatsqs');  <= sacarlas via sqs
$app->get('/cmpstatsdyn', \App\Controllers\CmpStatsController::class . ':cmpstatsdyn'); <= sacarlas de dinamo db
```

# CAMPAIGN 

Devuelven las camp simplificadas para el admin

`En ADMIN => NO SE USA` Esta opcion fue creada para el chatbot, pero se decidió que se quede como antes, el chat original.

```php

$app->get('/campaigns[/p/{p}/f/{f}/o/{o}/i/{i}]', \App\Controllers\CampaignController::class . ':listall');
$app->get('/campaign/{camp_id}', \App\Controllers\CampaignController::class . ':getCmp');
[
	{
		"camp_id": 435,
		"camp_name": "cincinnati",
		"active": "n"
	},
	{
		"camp_id": 433,
		"camp_name": "indianapolis",
		"active": "y"
	},
	{
		"camp_id": 436,
		"camp_name": "lexington",
		"active": "n"
	},
]
```
Esta son para PDI, devuelven una o mas camp con todos sus datos en un arreglo
Incluye relaciones "grouptz","caller_id_group" y "camp_schedule"

`En ADMIN => NO SE USA`

```php
$app->get('/cmps[/p/{p}/f/{f}/o/{o}/i/{i}]', \App\Controllers\CampaignController::class . ':listall');
$app->get('/cmp/{camp_id}', \App\Controllers\CampaignController::class . ':getCmp');
```
```json
[
	{
		"camp_id": 618,
		"camp_name": "Midwest 2 Predictive campaign 1",
		"tenantid": "173",
		"groupid": "0",
		"camp_description": "This is going to be the first phone banking campaign to target all the voters",
		"active": "n",
		"camp_type": "CL",
		"ratio": "1:1",
		"status": "0",
		"inbound_number": "_cmp618$$",
		"queue_name": "q17351781a4ac7c75e52",
		"maxretrys": "3",
		"waittime": "50",
		"callerid": "32423424234",
		"busyretrytime": "14000",
		"amdretrytime": "14400",
		"afterhourroute": "",
		"busycb": "y",
		"amdCB": "y",
		"noanswercb": "y",
		"noansretrytime": "28800",
		"timezones": "n",
		"invalidcb": "y",
		"invalidretrytime": "14400",
		"urlcall": "",
		"prepend": "1",
		"strip": "0",
		"dropcb": "y",
		"droptime": "14400",
		"adaptive_intensity": "20.00",
		"drop_limit": "3",
		"allow_inbound": "n",
		"calldataS": "<p><strong>Name {lead_fname} {lead_mname} {lead_lname}<\/strong><\/p>",
		"detectmachine": "1",
		"linked_campaign": "0",
		"brokencallback": "4",
		"customquotes": "0",
		"sqlfilter": "",
		"ordertype": "5",
		"didrotation": "1",
		"smsnumber": "",
		"posturlcall": "",
		"activist_codes": "",
		"multinumber": "0",
		"alternate_numbers": "0",
		"recordings": "0",
		"sla": "60",
		"created_at": "2023-02-09 03:33:34",
		"updated_at": "2023-02-09 03:33:34",
		"deleted_at": null,
		"cps": "100",
		"caller_id_group": null,
		"team_name": "midwest 2 team 1",
		"group_name": null,
		"camp_schedule": null
	}
]
```

Devuelve los conteos, toma el tenantid del user a traves del token

`En ADMIN => NO SE USA`

```php
$app->get('/campaigns/count', \App\Controllers\CampaignController::class . ':listall');
```
```json
{
	"total": 6,
	"active": 2,
	"off": 4
}
```
Busca campaña por nombre

`En ADMIN => NO SE USA`

```php
$app->get('/campaign_by_name/{camp_name}', \App\Controllers\CampaignController::class . ':listByName');
```
```json
{
	"camp_id": 425,
	"camp_name": "camp-name-cl",
	"tenantid": "138",
	"groupid": "162",
	"camp_description": "",
	"active": "y",
	"camp_type": "CL",
	"ratio": "3:1",
	"status": "0",
	"inbound_number": "_cmp425$$",
	"queue_name": "q1386e3a4a0156f23c96",
	"maxretrys": "9999",
	"waittime": "50",
	"callerid": "32423424234",
	"busyretrytime": "7200",
	"amdretrytime": "14400",
	"afterhourroute": "",
	"busycb": "y",
	"amdCB": "y",
	"noanswercb": "y",
	"noansretrytime": "28800",
	"timezones": "n",
	"invalidcb": "y",
	"invalidretrytime": "28800",
	"urlcall": "https:\/\/remotep.callevo.net\/aws_survey?id=11",
	"prepend": "1",
	"strip": "0",
	"dropcb": "y",
	"droptime": "14400",
	"adaptive_intensity": "4.00",
	"drop_limit": "3",
	"allow_inbound": "n",
	"calldataS": "<p><strong>Name {lead_fname} {lead_mname} {lead_lname}<\/strong><\/p>",
	"detectmachine": "0",
	"linked_campaign": "0",
	"brokencallback": "4",
	"customquotes": "0",
	"sqlfilter": "AND custom9 != ''",
	"ordertype": "2",
	"didrotation": "1",
	"smsnumber": "",
	"posturlcall": "",
	"multinumber": "0",
	"alternate_numbers": "0",
	"recordings": "1",
	"sla": "60",
	"created_at": "2022-10-20 14:08:08",
	"updated_at": "2024-09-25 11:00:07",
	"deleted_at": null,
	"cps": "0",
	"amdtransfer": "",
	"simulated": "0",
	"waitingrecordID": "0"
}
```

Para PDI estan en un arreglo

`En ADMIN => NO SE USA`

```php
$app->get('/campaign_no_actives', \App\Controllers\CampaignController::class . ':listNoActives');
```
```json
[
	{
		"camp_id": 426,
		"camp_name": "jjsctenanttestma"
	},
	{
		"camp_id": 890,
		"camp_name": "test in"
	},
	{
		"camp_id": 1354,
		"camp_name": "testcampaignjjsc"
	},
	{
		"camp_id": 1472,
		"camp_name": "cuca-la-loca-6-25-de-5"
	}
]
```

`En ADMIN => NO SE USA`
```php
$app->get('/campaign_actives', \App\Controllers\CampaignController::class . ':listActives');
```
```json
{
	"status": "ok",
	"message": [
		{
			"camp_id": 425,
			"camp_name": "camp-name-cl"
		},
		{
			"camp_id": 889,
			"camp_name": "jjsc.camp.cl.1"
		}
	]
}
```

`En ADMIN => NO SE USA`
```php
$app->get('/campaigns_non_manuals', \App\Controllers\CampaignController::class . ':getCampaignsNotManual');
```
```json
[
	{
		"camp_id": 433,
		"camp_name": "indianapolis"
	},
	{
		"camp_id": 434,
		"camp_name": "louisville"
	},
	{
		"camp_id": 435,
		"camp_name": "cincinnati"
	},
	{
		"camp_id": 436,
		"camp_name": "lexington"
	},
	{
		"camp_id": 594,
		"camp_name": "mcoinbound"
	}
]
```

Lista una o mas 

`En ADMIN => NO SE USA`
```php
$app->get('/campaign_schedule/{schedule_id}', \App\Controllers\CampaignController::class . ':getCampaignSchedule');
$app->get('/campaigns_schedule', \App\Controllers\CampaignController::class . ':getCampaignSchedule');
```
```json
{
	"status": "ok",
	"message": [
		{
			"schedule_id": 194,
			"camp_id": "432",
			"monday_active": "2",
			"monday_start": "08:00:00",
			"monday_stop": "21:00:00",
			"tuesday_start": "08:00:00",
			"tuesday_stop": "21:00:00",
			"wednesday_start": "08:00:00",
			"wednesday_stop": "21:00:00",
			"thursday_start": "08:00:00",
			"thursday_stop": "21:00:00",
			"friday_start": "08:00:00",
			"friday_stop": "21:00:00",
			"saturday_start": "08:00:00",
			"saturday_stop": "21:00:00",
			"sunday_start": "08:00:00",
			"sunday_stop": "21:00:00",
			"sunday_active": "2",
			"saturday_active": "2",
			"friday_active": "2",
			"thursday_active": "2",
			"wednesday_active": "2",
			"tuesday_active": "2",
			"updated_at": "2022-11-18 21:52:38",
			"campaign": {
				"camp_id": 432,
				"camp_name": "manual",
				"trunkID": "3",
				"camp_channels": "0",
				"ivrid": "0",
				"amdivrid": "0",
				"phoneID": "0",
				"tenantid": "139",
				"groupid": "81",
				"camp_description": "",
				"active": "n",
				"started": "00:00:00",
				"camp_type": "MA",
				"ratio": "3:1",
				"status": "0",
				"inbound_number": "_cmp432$$",
				"queue_name": "q13931d430198891daf0",
				"maxretrys": "5",
				"waittime": "50",
				"callerid": "2162387071",
				"busyretrytime": "7200",
				"amdretrytime": "14400",
				"startdialing": "00:00:00",
				"stopdialing": "00:00:00",
				"afterhourroute": "",
				"busycb": "y",
				"amdCB": "y",
				"noanswercb": "y",
				"noansretrytime": "28800",
				"timezones": "n",
				"invalidcb": "y",
				"invalidretrytime": "28800",
				"urlcall": "https:\/\/remotep.callevo.net\/?PAGE=salesforce\/sales",
				"prepend": "1",
				"strip": "0",
				"dropcb": "y",
				"droptime": "14400",
				"customfield": "custom",
				"customlabel": "",
				"notifychannel": "",
				"notifytime": "30",
				"showcustomfield": "n",
				"notifyholding": "n",
				"forcedisposition": "n",
				"showdisp": "n",
				"defaultdisp": "0",
				"adaptive_dl_diff_target": "0",
				"adaptive_intensity": "0.00",
				"drop_limit": "3",
				"allow_inbound": "n",
				"agentcmp": "0",
				"calldataS": "<p>Name {lead_fname} {lead_mname} {lead_lname}<\/p>",
				"calldataF": "",
				"callDataN": "",
				"inlinecallid": "y",
				"useautostart": "n",
				"buildrange": "",
				"minconnrate": "90",
				"demo": "0",
				"demoduration": "30",
				"democonnrate": "8",
				"fetcherwaittime": "1000",
				"brokenCB": "4",
				"linesdialed": "0",
				"talktime_alarm": "30",
				"talktime_color": "7382763",
				"timenoready": "20",
				"timenoready_color": "15536915",
				"timebreak": "30",
				"timebreak_color": "15887894",
				"timelunch": "30",
				"timelunch_color": "15780361",
				"timewrap": "15",
				"timewrap_color": "3407749",
				"goals": "0",
				"goalstype": "1",
				"expectedwaittime": "25",
				"waitingtime_alarm": "30",
				"waittime_color": "2208526",
				"detectmachine": "0",
				"initialrecordID": "0",
				"finalrecordID": "0",
				"agentammmessage": "0",
				"agentofflinemessage": "0",
				"pressonekey": "1",
				"linked_campaign": "0",
				"brokencallback": "4",
				"customquotes": "0",
				"recordcalls": "n",
				"tzscrubid": "3",
				"pepperclient": "callbacks",
				"sqlfilter": "",
				"timeother": "0",
				"timeother_color": "0",
				"timebathroom": "0",
				"timebathroom_color": "0",
				"timemeeting": "0",
				"timemeeting_color": "0",
				"ordertype": "2",
				"didrotation": "1",
				"smsnumber": "",
				"posturlcall": "",
				"qcenabled": "y",
				"usedncglobal": "y",
				"usecmpdnc": "y",
				"usecampdncfrom": "y",
				"calltimeid": "99",
				"qcurl": "",
				"integration_type": "4",
				"two_way_integration": "0",
				"activist_codes": "",
				"van_type": "0",
				"multinumber": "0",
				"alternate_numbers": "0",
				"recordings": "0",
				"sla": "60",
				"created_at": "2022-11-18 21:52:38",
				"updated_at": "2024-06-14 16:33:03",
				"deleted_at": null,
				"cps": "1",
				"logo": null,
				"logotype": null,
				"agentmessage": null,
				"show_alert": "7",
				"amdtransfer": "",
				"simulated": "0",
				"waitingrecordID": "0"
			}
		},
		.
	]
}
```

`En ADMIN => ` Obtiene la lista de surveys generados por el script builder para asignarlos a la campaña. En los `screens de wizard new campaign y campaign edit`.

```php
$app->get('/campaign_surveys/{camp_id}', \App\Controllers\CampaignController::class . ':getCampaignSurveys');
```
```json
{
	"status": "ok",
	"message": [
		{
			"surveyid": 69,
			"survey_name": "fiapaclicker",
			"description": "fiapa clicker survey",
			"url": "https:\/\/remotep.callevo.net\/aws_survey?id=69"
		},
		{
			"surveyid": 78,
			"survey_name": "mifiac3purged",
			"description": "",
			"url": "https:\/\/remotep.callevo.net\/aws_survey?id=78"
		},
		{
			"surveyid": 81,
			"survey_name": "TestScriptforBrendan",
			"description": "Test",
			"url": "https:\/\/remotep.callevo.net\/aws_survey?id=81"
		},
		{
			"surveyid": 82,
			"survey_name": "fiapaclicker-Copy",
			"description": "fiapa clicker survey",
			"url": "https:\/\/remotep.callevo.net\/aws_survey?id=82"
		}
	]
}
```

`En ADMIN => ` Obtiene la lista de los External Scripts. En los `screens de wizard new campaign y campaign edit`.

```php
$app->get('/campaign_scripts[/{camp_id}]', \App\Controllers\CampaignController::class . ':getCampaignSurveys');
```
```json
{
	"status": "ok",
	"message": [
		{
			"surveyid": 2916,
			"survey_name": "q2_sp - s1087nnf\/q2_sp",
			"description": "q2_sp",
			"url": "https:\/\/remotep.callevo.net\/?PAGE=s1087nnf\/q2_sp"
		},
		{
			"surveyid": 3444,
			"survey_name": "start - s1251n2r\/start",
			"description": "start",
			"url": "https:\/\/remotep.callevo.net\/?PAGE=s1251n2r\/start"
		},
		{
			"surveyid": 4208,
			"survey_name": "start - s2171n2f\/start",
			"description": "start",
			"url": "https:\/\/remotep.callevo.net\/?PAGE=s2171n2f\/start"
		},
	]
}
```

Lista las camp activas donde esta el agente trabajando

`En ADMIN => NO SE USA`.

```php
$app->get('/campaigns_agent/{agentid}', \App\Controllers\CampaignController::class . ':campaignsAgent');
```
```json
{
	"status": "ok",
	"message": [
		{
			"camp_id": "434",
			"camp_name": "louisville",
			"camp_type": "CL"
		}
	]
}
```

Lista los agentes que estan en la campaña activa

`En ADMIN => NO SE USA`.

```php
$app->get('/agents_campaign/{camp_id}', \App\Controllers\CampaignController::class . ':agentsCampaign');
```
```json
{
	"status": "ok",
	"message": [
		{
			"agentid": "5649",
			"agent_code": "u139136a37bcac64769a",
			"name": "mco01"
		},
		{
			"agentid": "5650",
			"agent_code": "u13901fe4caf2627045a",
			"name": "mco02"
		},
		{
			"agentid": "5651",
			"agent_code": "u139e6348f2025b8f69e",
			"name": "mco03"
		},
		
	]
}
```

Ruta para PDI

`En ADMIN => NO SE USA`.

```php
$app->post('/create_campaign', \App\Controllers\CampaignController::class . ':modifyCmp');
```
```json
{
	"camp_id": "-1",
	"camp_name": "pdi_cl_test_camp_by_route_3",
	"camp_description": "",
	"camp_type": "CL",
	"ratio": "1:1",
	"inbound_number": "",
	"queue_name": "pdi_test_cl_2",
	"maxretrys": "5",
	"waittime": "50",
	"callerid": "32423424234",
	"didrotation": "1",
	"busyretrytime": "14000",
	"busycb": "y",
	"amdretrytime": "14400",
	"amdCB": "y",
	"noanswercb": "y",
	"noansretrytime": "28800",
	"timezones": "n",
	"invalidcb": "y",
	"invalidretrytime": "14400",
	"urlcall": "https://remotep.callevo.net/?PAGE=T25C2/roust",
	"dropcb": "y",
	"droptime": "14400",
	"drop_limit": "3",
	"calldataS": "<p><strong>Name {lead_fname} {lead_mname} {lead_lname}</strong></p>",
	"talktime_alarm": "30",
	"talktime_color": 7382763,
	"timenoready": "20",
	"timenoready_color": 15536915,
	"timebreak": "30",
	"timebreak_color": 15887894,
	"timelunch": "30",
	"timelunch_color": 15780361,
	"timewrap": "15",
	"timewrap_color": 3407749,
	"waitingtime_alarm": "30",
	"waittime_color": 2208526,
	"detectmachine": "1",
	"ordertype": "5",
	"posturlcall": "",
	"alternate_numbers": "0",
	"recordings": "0",
	"linked_campaign": "",
	"sqlfilter": ""
}
```


Devuelve listado paginado

`ADMIN =>` Se utiliza en la opcion `screen de projects` lista todas las campañas del tenant, paginado y filtrado por status.


```php
$app->post('/cmps_range[/p/{p}/i/{i}]', \App\Controllers\CampaignController::class . ':listall');
```
```json
{
	"status": "ok",
	"message": {
		"total_records": 4,
		"record_start": 1,
		"page": "1",
		"total_pages": 1,
		"page_length": "5",
		"data": [
			{
				"camp_id": "425",
				"camp_name": "camp name",
				"tenantid": "138",
				"groupid": "162",
				"camp_description": "",
				"active": "n",
				"camp_type": "CL",
				"ratio": "3:1",
				"status": "0",
				"inbound_number": "_cmp425$$",
				"queue_name": "q1386e3a4a0156f23c96",
				"maxretrys": "9999",
				"waittime": "50",
				"callerid": "32423424234",
				"busyretrytime": "7200",
				"amdretrytime": "14400",
				"afterhourroute": "",
				"busycb": "y",
				"amdCB": "y",
				"noanswercb": "y",
				"noansretrytime": "28800",
				"timezones": "n",
				"invalidcb": "y",
				"invalidretrytime": "28800",
				"urlcall": "https:\/\/remotepdev.callevo.net\/index.php?PAGE=roust\/roust",
				"prepend": "1",
				"strip": "0",
				"dropcb": "y",
				"droptime": "14400",
				"adaptive_intensity": "3.00",
				"drop_limit": "3",
				"allow_inbound": "n",
				"calldataS": "<p><strong>Name {lead_fname} {lead_mname} {lead_lname}<\/strong><\/p>",
				"detectmachine": "0",
				"linked_campaign": "0",
				"brokencallback": "4",
				"customquotes": "0",
				"sqlfilter": "",
				"ordertype": "2",
				"didrotation": "2",
				"smsnumber": "",
				"posturlcall": "",
				"activist_codes": "",
				"multinumber": "0",
				"alternate_numbers": "0",
				"recordings": "1",
				"sla": "60",
				"created_at": "2022-10-20 14:08:08",
				"updated_at": "2023-11-11 03:00:08",
				"deleted_at": null,
				"cps": "0",
				"team_name": "jjsc_tenant_test_team",
				"team_id": 1005,
				"group_name": "test",
				"camp_schedule": {
					"schedule_id": 186,
					"camp_id": "425",
					"monday_active": "2",
					"monday_start": "08:00:00",
					"monday_stop": "21:00:00",
					"tuesday_start": "08:00:00",
					"tuesday_stop": "21:00:00",
					"wednesday_start": "08:00:00",
					"wednesday_stop": "21:00:00",
					"thursday_start": "07:00:00",
					"thursday_stop": "21:00:00",
					"friday_start": "07:00:00",
					"friday_stop": "21:00:00",
					"saturday_start": "08:00:00",
					"saturday_stop": "21:00:00",
					"sunday_start": "08:00:00",
					"sunday_stop": "21:00:00",
					"sunday_active": "2",
					"saturday_active": "2",
					"friday_active": "1",
					"thursday_active": "1",
					"wednesday_active": "2",
					"tuesday_active": "2",
					"updated_at": "2023-10-27 12:53:07"
				}
			},
		]
	}
}
```

Ruta para PDI

`En ADMIN => NO SE USA`.

```php
$app->post('/cmp', \App\Controllers\CampaignController::class . ':modifyCmp');
$app->put('/cmp[/{camp_id}]', \App\Controllers\CampaignController::class . ':modifyCmp');
```
```json
{
  "camp_id": 0,
  "camp_name": "ak 0217 v11",
  "tenantid": 0,
  "active": "",
  "camp_type": "CL",
  "ratio": "2:1",
  "status": 0,
  "inbound_number": "",
  "queue_name": "q2006d17be53085e2819",
  "maxretrys": 5,
  "waittime": 70,
  "callerid": "2135551212",
  "afterhourroute": "",
  "busycb": "y",
  "amdCB": "y",
  "invalidcb": "y",
  "noanswercb": "y",
  "dropcb": "y",
  "busyretrytime": 14400,
  "amdretrytime": 14400,
  "noansretrytime": 14400,
  "droptime": 28800,
  "drop_limit": 0,
  "invalidretrytime": 0,
  "urlcall": "https://webadmindev.callevo.net/remotep?PAGE=500001ak_0217_v11/500001ak_0217_v11_Script&CALLID={callid}",
  "calldataS": "        <P><B>Name {lead_fname} {lead_mname} {lead_lname}</B></P>        <P><B>Party {party} Sex {gender} Age {age} PVBM {permav}</B></P>",
  "detectmachine": 1,
  "linked_campaign": 0,
  "brokencallback": 0,
  "sqlfilter": "",
  "talktime_alarm": 30,
  "talktime_color": 10274556,
  "timenoready": 900,
  "timenoready_color": 10066431,
  "timebreak": 900,
  "timebreak_color": 10066431,
  "timelunch": 900,
  "timelunch_color": 10066431,
  "timewrap": 20,
  "timewrap_color": 16750848,
  "waitingtime_alarm": 120,
  "waittime_color": 16776960,
  "timeother": 0,
  "timeother_color": 0,
  "timebathroom": 0,
  "timebathroom_color": 0,
  "timemeeting": 0,
  "timemeeting_color": 0,
  "ordertype": 0,
  "didrotation": 0,
  "smsnumber": "",
  "posturlcall": "",
  "multinumber": 0,
  "alternate_numbers": 0,
  "recordings": 0,
  "sla": 0,
  "created_at": "2023-18-02 1812:20:20",
  "updated_at": "2023-18-02 1812:20:20",
  "deleted_at": "",
  "cps": 0
}
```

Agrega o modifica campaña

`En ADMIN => ` Se utiliza en `new campaign`, `campaign edit`, para actualizar la campaña, normalmente se envia todo el objeto que fue enviado a la carga de los datos `GET/campaign/id` con los datos modificados, tambien en `activity`, `livestats` para cuando realizan un cambio en intensity, se usa tambien el el `importer` para poder traer la lista de campañas y filtrar por `van_type > 0` .

```php
$app->post('/campaign', \App\Controllers\CampaignController::class . ':modifyCmp');
$app->put('/campaign[/{camp_id}]', \App\Controllers\CampaignController::class . ':modifyCmp');
```
```json
{
	"camp_id": "-1",
	"camp_name": "pdi_cl_test_camp_by_route_1_modif",
	"camp_description": "description",
	"ratio": "2:1",
	"recordings": "1",
	"sqlfilter": "",
	"campaign_schedule": {
		"monday_active": 1,
		"tuesday_active": 1,
		"wednesday_active": 1,
		"thursday_active": 1,
		"friday_active": 1,
		"saturday_active": 1,
		"sunday_active": 1,
		"monday_start": "08:00:00",
		"tuesday_start": "08:00:00",
		"wednesday_start": "08:00:00",
		"thursday_start": "08:00:00",
		"friday_start": "08:00:00",
		"saturday_start": "08:00:00",
		"sunday_start": "08:00:00",
		"monday_stop": "18:00:00",
		"tuesday_stop": "18:00:00",
		"wednesday_stop": "23:00:00",
		"thursday_stop": "23:00:00",
		"friday_stop": "23:00:00",
		"saturday_stop": "18:00:00",
		"sunday_stop": "18:00:00"
	  }
}
```

Agrega y modifica calendario de start/stop para las campañas

`ADMIN => NO SE USA`

```php
$app->post('/campaign_schedule', \App\Controllers\CampaignController::class . ':modifyCampaignSchedule');
$app->put('/campaign_schedule/{schedule_id}', \App\Controllers\CampaignController::class . ':modifyCampaignSchedule');
```
```js
campaign.campaign_schedule = {
	monday_active: $("#schedule_active_mon option:selected").val(),
	tuesday_active: $("#schedule_active_tue option:selected").val(),
	wednesday_active: $("#schedule_active_wed option:selected").val(),
	thursday_active: $("#schedule_active_thu option:selected").val(),
	friday_active: $("#schedule_active_fri option:selected").val(),
	saturday_active: $("#schedule_active_sat option:selected").val(),
	sunday_active: $("#schedule_active_sun option:selected").val(),
	monday_start: setTimeFormat($("#start_mon").val()),
	tuesday_start: setTimeFormat($("#start_tue").val()),
	wednesday_start: setTimeFormat($("#start_wed").val()),
	thursday_start: setTimeFormat($("#start_thu").val()),
	friday_start: setTimeFormat($("#start_fri").val()),
	saturday_start: setTimeFormat($("#start_sat").val()),
	sunday_start: setTimeFormat($("#start_sun").val()),
	monday_stop: setTimeFormat($("#stop_mon").val()),
	tuesday_stop: setTimeFormat($("#stop_tue").val()),
	wednesday_stop: setTimeFormat($("#stop_wed").val()),
	thursday_stop: setTimeFormat($("#stop_thu").val()),
	friday_stop: setTimeFormat($("#stop_fri").val()),
	saturday_stop: setTimeFormat($("#stop_sat").val()),
	sunday_stop: setTimeFormat($("#stop_sun").val()),
};
```

`ADMIN => NO SE USA`

```php
$app->put('/campaign_generate_ivr/{camp_id}', \App\Controllers\CampaignController::class . ':genIvr');
```

Estas rutas usan los SP y estan usadas via NATS

`ADMIN => NO SE USA`

```php
$app->post('/startcampaign/{camp_id}', \App\Controllers\CampaignController::class . ':startstop');
$app->post('/stopcampaign/{camp_id}', \App\Controllers\CampaignController::class . ':startstop');
```

Borra calendario

`ADMIN => NO SE USA`

```php
$app->delete('/campaign_schedule[/{schedule_id}]', \App\Controllers\CampaignController::class . ':deleteCampaignSchedule');
$app->delete('/campaign[/{camp_id}]', \App\Controllers\CampaignController::class . ':deleteC');
$app->delete('/cmp[/{camp_id}]', \App\Controllers\CampaignController::class . ':deleteCmp');
```

# DISPOSITION

Recupera disp por campaña

`ADMIN => ` Se usa en `Search by Call` y `Calls History` para el dropdown de projects. 

```php
$app->get('/disposition_by_campaign/{camp_id}', \App\Controllers\DispositionController::class . ':getDispositionByCampaign');
```
parametros de entrada:
```json
 {
    "report_id": "dispositions_by_campaign",
    "title": "Dispositions Summary by Campaign",
    "output": "json",
    "header": [
        {
            "showas": "",
            "source": "DATE",
            "caption": "Date",
            "class": "text-center",
            "width": "10%",
            "isTotal": "false"
        },
        {
            "showas": "",
            "source": "CAMPAIGN",
            "caption": "Campaign",
            "class": "text-left",
            "width": "",
            "isTotal": "false"
        },
        {
            "showas": "",
            "source": "Handled_by",
            "caption": "Handled by",
            "class": "text-left",
            "width": "",
            "isTotal": "false"
        },
        {
            "showas": "",
            "source": "CallDisposition",
            "caption": "Call Disposition",
            "class": "text-left",
            "width": "",
            "isTotal": "false"
        },
        {
            "showas": "",
            "source": "TotalCalls",
            "caption": "Total Calls",
            "class": "text-right",
            "width": "10%",
            "isTotal": "true"
        },
			 {
            "showas": "",
            "source": "AvgDuration",
            "caption": "Avg Duration",
            "class": "text-right",
            "width": "10%",
            "isTotal": "true"
        }
    ],
    "where": "DATE >='2024-02-23' AND DATE <='2024-02-23'  AND camp_id=433"
}
```
Salida:
```json
[
	{
		"dcid": 14995,
		"dispid": "2399",
		"camp_id": "433",
		"clientcode": "",
		"qcenabled": "n",
		"disposition": {
			"dispid": 2399,
			"statusid": "1",
			"dispcode": "MANUAL",
			"dispdesc": "Manual call",
			"success": "n",
			"contact": "n",
			"presentation": "n",
			"dnc": "n",
			"enabled": "y",
			"finalcrc": "n",
			"recall": "n",
			"recallscale": "0",
			"seconds": "0",
			"rollover": "n",
			"rocamp_id": "0",
			"revenue": "0.00",
			"crcid": "0",
			"tenantid": "139",
			"created_at": "2022-11-18 20:34:36",
			"updated_at": "2022-11-18 20:34:36",
			"deleted_at": null,
			"vanresultid": "0",
			"integration_type": "0"
		}
	},
	{
		"dcid": 14997,
		"dispid": "2401",
		"camp_id": "433",
		"clientcode": "",
		"qcenabled": "n",
		"disposition": {
			"dispid": 2401,
			"statusid": "1",
			"dispcode": "NH",
			"dispdesc": "Not home\/not convenient",
			"success": "n",
			"contact": "n",
			"presentation": "n",
			"dnc": "n",
			"enabled": "y",
			"finalcrc": "n",
			"recall": "y",
			"recallscale": "0",
			"seconds": "28800",
			"rollover": "n",
			"rocamp_id": "0",
			"revenue": "0.00",
			"crcid": "0",
			"tenantid": "139",
			"created_at": "2022-11-18 20:34:36",
			"updated_at": "2022-11-18 20:34:36",
			"deleted_at": null,
			"vanresultid": "0",
			"integration_type": "0"
		}
	},
]
```

Recupera dispo para el dialogo 

`ADMIN => ` Se utiliza en el `screen de Projects` en el botón `Disposition` que muestra un popup con esta información. Y puede seleccionar con dos criterios `Used CRCS` y  `QC Enabled`


```php
$app->get('/campaign_disposition/{camp_id}', \App\Controllers\CampaignController::class . ':getCampaignDisposition');
```
```json
[
	{
		"dcid": 1163,
		"dispid": "1184",
		"camp_id": "288",
		"clientcode": "",
		"qcenabled": "n",
		"disposition": {
			"dispid": 1184,
			"statusid": "1",
			"dispcode": "DNC",
			"dispdesc": "Internal_DNC",
			"success": "n",
			"contact": "y",
			"presentation": "y",
			"dnc": "y",
			"enabled": "y",
			"finalcrc": "y",
			"recall": "n",
			"recallscale": "0",
			"seconds": "0",
			"rollover": "n",
			"rocamp_id": "0",
			"revenue": "0.00",
			"crcid": "0",
			"tenantid": "98",
			"created_at": "2022-03-10 17:45:05",
			"updated_at": "2022-05-31 21:04:47",
			"deleted_at": null,
			"vanresultid": "0",
			"integration_type": "0"
		}
	},
	{
		"dcid": 1165,
		"dispid": "1188",
		"camp_id": "288",
		"clientcode": "",
		"qcenabled": "n",
		"disposition": {
			"dispid": 1188,
			"statusid": "1",
			"dispcode": "DEC",
			"dispdesc": "DECEASED",
			"success": "n",
			"contact": "y",
			"presentation": "n",
			"dnc": "n",
			"enabled": "y",
			"finalcrc": "y",
			"recall": "n",
			"recallscale": "0",
			"seconds": "0",
			"rollover": "n",
			"rocamp_id": "0",
			"revenue": "0.00",
			"crcid": "0",
			"tenantid": "98",
			"created_at": "2022-03-10 17:45:05",
			"updated_at": "2022-05-31 21:04:47",
			"deleted_at": null,
			"vanresultid": "0",
			"integration_type": "0"
		}
	},
]
```



Modifica disposiciones para campaña

`ADMIN => ` Guarda las disposiciones seleccionadas en los dos criterios `Used CRCS` y  `QC Enabled`

```php
$app->put('/campaign_disposition[/{camp_id}]', \App\Controllers\CampaignController::class . ':modifyCampaignDisposition');
```
```js
{
	campdisp : [
		{
			dispid: id,
			qcenabled: qccheck,
		},
		.
	]
}
```

Rutas para PDI

`ADMIN => NO SE USA`

```php
$app->get('/disp/{dispid}', \App\Controllers\DispositionController::class . ':getDispo');
```
```json
[
	{
		"dispid": 6961,
		"statusid": "6",
		"dispcode": "AMM",
		"dispdesc": "Answering machine (agent detected)",
		"success": "n",
		"contact": "n",
		"presentation": "n",
		"dnc": "n",
		"enabled": "y",
		"finalcrc": "n",
		"recall": "y",
		"recallscale": "0",
		"seconds": "14400",
		"rollover": "n",
		"rocamp_id": "0",
		"revenue": "0.00",
		"crcid": "0",
		"tenantid": "200",
		"created_at": "2023-02-15 20:35:33",
		"updated_at": "2023-02-15 20:35:33",
		"deleted_at": null,
		"vanresultid": "0",
		"integration_type": "0",
		"status": {
			"statusid": 6,
			"statusname": "Answer Machine",
			"resetable": "1",
			"exportable": "0",
			"order": "99"
		}
	},
	
]
```

Paginado

`ADMIN => NO SE USA`

```php
$app->get('/disps[/p/{p}/f/{f}/o/{o}/i/{i}]', \App\Controllers\DispositionController::class . ':listall');
```
```json
[
	{
		"dispid": 2379,
		"dispcode": "MANUAL",
		"dispdesc": "Manual call",
		"success": "n",
		"contact": "n",
		"presentation": "n",
		"dnc": "n",
		"enabled": "y",
		"finalcrc": "n",
		"recall": "n",
		"seconds": "0",
		"rollover": "n",
		"rocamp_id": "0",
		"revenue": "0.00",
		"crcid": "0",
		"created_at": "2022-10-19 14:39:08",
		"updated_at": "2022-10-19 14:39:08",
		"status": {
			"statusid": 1,
			"statusname": "Person",
			"resetable": "1",
			"exportable": "0",
			"order": "1"
		}
	},
	
]	
```

Agrega/Modifica disposiciones

`ADMIN => NO SE USA`

```php
$app->post('/disp', \App\Controllers\DispositionController::class . ':modifyDisposition');
$app->put('/disp', \App\Controllers\DispositionController::class . ':modifyDisposition');
```
```json
{
	"dispid":0,
	"dispcode":"AMM",
	"dispdesc":"Answering machine",
	"success":"n",
	"contact":"n",
	"presentation":"n",
	"dnc":"n",
	"enabled":"y",
	"finalcrc":"n",
	"recall":"y",
	"recallscale":"0",
	"seconds":6,
	"rollover":"",
	"rocamp_id":0,
	"revenue":"0",
	"crcid":"0",
	"tenantid":0,
	"CreatedAt":"",
	"UpdatedAt":"",
	"DeletedAt":"",
	"VanresultID":"",
	"IntegrationType":"",
	"statusid":6
}
```
Borra

`ADMIN => NO SE USA`

```php
$app->delete('/disp/{id}', \App\Controllers\DispositionController::class . ':deleteDisposition');
```


Rutas para ADMIN

`ADMIN => NO SE USA` En el screen `Disposition` se obtiene la información por modelos propios del admin. 

```PHP
$app->get('/disposition/{dispid}', \App\Controllers\DispositionController::class . ':getDispo');
$app->get('/dispositions[/p/{p}/f/{f}/o/{o}/i/{i}]', \App\Controllers\DispositionController::class . ':listall')->setName('disposition');
```

Salida igual a la PDI disps pero sin paginar

Agrega/Modifica

`ADMIN => ` En el screen `Disposition Edit` envia por medio de un form action cuando se acciona el boton de tipo submit. 

```PHP
$app->post('/disposition', \App\Controllers\DispositionController::class . ':modifyDisposition');
$app->put('/disposition', \App\Controllers\DispositionController::class . ':modifyDisposition');
```
```json
{
  "campdisp": [],
  "dispid": "-1",
  "dispcode": "TEST1",
  "dispdesc": "TEST ONLY1",
  "success": "n",
  "contact": "n",
  "presentation": "n",
  "dnc": "n",
  "enabled": "n",
  "statusid": "-1",
  "finalcrc": "n",
  "recall": "n",
  "recallscale": "0",
  "seconds": "0",
  "rollover": "n",
  "rocamp_id": "206",
  "revenue": "0",
  "crcid": "0",
  "cookie": "",
  "integration_type": "0"
}
```

Borra dispositions actualiza survey y campaigns 

`ADMIN => ` En el screen `Dispositions` al seleccionar un item o registro le permite eliminar . 

```PHP
$app->delete('/disposition/{id}', \App\Controllers\DispositionController::class . ':deleteDisposition');
```

`ADMIN => NO SE USA`
```PHP
$app->delete('/dispositions', \App\Controllers\DispositionController::class . ':deleteDisposition');
```

# DNC 

`ADMIN => ` Se utiliza en el screen `Dnc Global Edit` para traer el record de dnc y se llena el phone, la campaña y la razon.

```PHP
$app->get('/dnc/{id}', \App\Controllers\DncController::class . ':getDnc');
```

`ADMIN => ` Se utiliza en DNS Global screen para listar todos los `Do Not Call`. Primero se debe seleccionar si es Global -> Yes/No, Cuando es `Global No`, se selecciona la campaña y se ingresa el `phone` se buscar, luego se ejecuta esta ruta

```PHP
$app->get('/dnccomplain/search/{camp_id}/{phone}', \App\Controllers\DncController::class . ':dncComplainSearch');
```
```json
[
	{
		"dncic": 4,
		"cdncid": "0",
		"camp_id": "39",
		"tenantid": "98",
		"dncImported": "2022-02-11 21:19:08",
		"phonenumber": "4052850223",
		"dncchange": "",
		"action": "A",
		"source": null,
		"note": "api55 camp 39"
	},
	{
		"dncic": 119883,
		"cdncid": "0",
		"camp_id": "39",
		"tenantid": "98",
		"dncImported": "2014-12-08 18:56:29",
		"phonenumber": "4052850223",
		"dncchange": "2014-12-08T18:56",
		"action": "I",
		"source": null,
		"note": null
	},
	
]
```

`ADMIN => NO SE USA YA`
```php
$app->get('/dncsglobal[/{camp_id}]', \App\Controllers\DncController::class . ':dncglobalListAll');
$app->get('/dncglobal/{id}', \App\Controllers\DncController::class . ':getDncglobal');
```

`ADMIN => ` Se utiliza en DNS Global screen para listar todos los `Do Not Call`. Primero se debe seleccionar si es Global -> Yes/No, Cuando es `Global Yes`, se ingresa el `phone` se buscar, luego se ejecuta esta ruta
```php
$app->get('/dncglobal/search/{data}', \App\Controllers\DncController::class . ':getDncglobalSearch');
```
```json
[
	{
		"dncid": 11,
		"tenantid": "98",
		"cdncid": "0",
		"phone": "2055292756",
		"status": "y",
		"reason": "Dispositioned as DNC",
		"created_at": "2022-03-06 00:00:00",
		"updated_at": null,
		"deleted_at": null
	},
	
]
```
Actualiza o crea un DNC

`ADMIN => ` Se utiliza en `DNS Global Edit` screen para guardar los cambios realizados en los campos global (Y/N), phone, campaign, reason.
```php
$app->post('/dnc', \App\Controllers\DncController::class . ':modifyDnc');
$app->put('/dnc[/{id}]', \App\Controllers\DncController::class . ':modifyDnc');
```
body:
```js
{
	"id": dncid, 
	"dest": by == 1 ? "global" : "camp", 
	"tenantid": parseInt( $("#tenantid").val() ),
	"camp_id": campid,
	"phone": phone,
	"text": reason,
	"status": $('#status').is(':checked') ? 'y' : 'n'
}
```

`ADMIN => YA NO SE USA` 
```php
$app->post('/dncglobal[/{id}]', \App\Controllers\DncController::class . ':modifyDncglobal');
$app->put('/dncglobal[/{id}]', \App\Controllers\DncController::class . ':modifyDncglobal');
```


Llena DNC usando un file segun parametros de entrada

`ADMIN => ` Screen `DNC` ejecutado por medio del boton `Import`. Presenta un screen para importar un archivo, seleccionando tambien, si es Global (Y/N), campaign, reason. El proceso es cargar el archivo, codificarlos con base64 
```php
$app->post('/dncglobalupload', \App\Controllers\DncController::class . ':importDncglobal');
```
```js
{
	global: 1,
	tenantid: $("#tenantid").val(),
	reason: $('#reason').val(),
	camp_id: $("#camp_id option:selected").val(),
	status: $('#status').is(':checked') ? 'y' : 'n',
	filename: $('#file').val(),
    csv: encodeBase64(filecontent)
}
```
formato del archivo a ser importado
```
PHONE
23223423
234242323
```

Borra dnc por id

`ADMIN => ` Para eliminar un registro/phone en DNC se debe primero seleccionar si es global o no, campaña y numero de phone completo o en parte, Se debe seleccionar para luego eliminarlo.
```php
$app->delete('/dncglobal/{id}', \App\Controllers\DncController::class . ':deleteDncglobal');
```

`ADMIN => YA NO SE USA` 
```php
$app->delete('/dnc/{id}', \App\Controllers\DncController::class . ':deleteDnc');
```

# ALERTAS 


Busca alertas
`ADMIN => ` Función `alerts()` en `leads/resources/views/templates/app.twig` que corre al inicio luego del login para traer todas las alertas del sistema. Si existen alarmas el icono de campana parpadeará.

```php
$app->get('/alerts', \App\Controllers\AlertsController::class . ':alerts');
```
```json
{
	"status": "ok",
	"message": [
		{
			"type": "DIALTABLE",
			"source": "CAMPAIGN",
			"idx": 3,
			"status": "med",
			"msg": "2 Campaign(s) does not have at least one started list",
			"data": [
				{
					"camp_id": 13,
					"message": "Camp name testsborjacl has no pool started"
				},
				{
					"camp_id": 31,
					"message": "Camp name camptest2 has no pool started"
				}
			]
		},
		{
			"type": "RESET",
			"source": "POOL",
			"idx": 3,
			"status": "med",
			"msg": "4 Lists have no eligible records",
			"data": [
				{
					"camp_id": 10,
					"poolid": 40,
					"message": "List minagent_file.csv does not have elegible records"
				},
				{
					"camp_id": 31,
					"poolid": 360,
					"message": "List redistrictingmoderates2.csv does not have elegible records"
				},
				{
					"camp_id": 10,
					"poolid": 39,
					"message": "List ricktestnumbers.csv does not have elegible records"
				},
				{
					"camp_id": 10,
					"poolid": 41,
					"message": "List testnumbersaws1.csv does not have elegible records"
				}
			]
		}
	]
}	
```

Chequea alert en DNC

`ADMIN => NO SE USA`.

```php
$app->get('/alert_dnc', \App\Controllers\DncController::class . ':alertDNC');
 [
	 "type" => "DNC",
	 "source" => "DNC GLOBAL|DNC_COMPLAIN",
	 "idx" => 1,
	 "status"=>"low", 
	 "msg"=>"$count_dnc DNC Global numbers have been added or updated today.",
	 "data"=>$arr
];
```

`ADMIN => NO SE USA`.

```php
$app->get('/alert_pools', \App\Controllers\PoolController::class . ':alertPool');
```
```js
Alerta y mascara
// Contar pools con mas de tres meses de creados 0b00000001;
// Contar pools que no han sido start hace 2 meses 0b00000010;
// Contar pools que no tienen elegibles 0b00000100;
// Contar pools que no han sido reset hace 4 meses o nunca 0b00001000;
// Contar pools que no han sido importados 0b00010000;
{
	"type": "DIALTABLE",
	"source": "CAMPAIGN",
	"idx": 3,
	"status": "med",
	"msg": "2 Campaign(s) does not have at least one started list",
	"data": [
		{
			"camp_id": 13,
			"message": "Camp name testsborjacl has no pool started"
		},
		{
			"camp_id": 31,
			"message": "Camp name camptest2 has no pool started"
		}
	]
},
```

Crea una mascara de bits para usar en el campo show_alert de las tablas
- dnc_global
- dnc_complain
- pools
- dialer_campaings


`ADMIN => ` Con esta ruta el usuario puede ignorar las alertas de forma permanente hasta que revoque esa desicion.

```php
$app->post('/ignore_alerts', \App\Controllers\AlertsController::class . ':ignoreAlerts');
```
parametro de entrada
```json
{
    "data": [
        {
            "type": "DIALTABLE",
            "source": "POOL",
            "idx": "1",
            "data": [
                {
                    "camp_id": "355",
                    "poolid": "346"
                }
            ]
        }
    ]
}
```
devuelve 
```json
{
	"status": "ok",
	"message": "Done"
}
```
Resetea las mascaras de bits de todos los campos de alertas

`ADMIN => ` Con esta ruta el usuario puede recuperar o reestablecer las alertas.

```php
$app->post('/retrieve_all_alerts', \App\Controllers\AlertsController::class . ':retrieveAllAlerts');
```

# IMPORTADORES (no pools) 

Importa users desde un file

`ADMIN => ` Screen `Users Importer` permite importar un archivo con usuarios en el formato abajo descrito.

```php
$app->post('/import_users', \App\Controllers\UserController::class . ':importerUsers');
```
Data que se envia
```js
{
	tenantid: usertype==2 || usertype==36 || usertype==37 ? $("#tenantid option:selected").val() : tenantid, 
	filename: $('#file').val(),
	csv: encodeBase64(filecontent)
};
```

- Username es generado, se usa cualquier cosa que se ponga en el primer campo se ignora
- Si no se especigica el usertype se asume 27
- Si el tenantid se omite se toma el del token del user que esta haciendo el upload
- Si el fullname se omite se pone el email como fullname
- Si el email debe ser valido
- No se crea entradas en Cognito, cuando el user se logea por primera vez debe especificar el passwd

formato:
```
username,fullname,email,usertype,language,tenantid
NONE,admin,NONE,,27,en,25
GENERATE,super,,cuco1@cuco.com,35,en,25
,Test agent,,,,en,
```

Esto son sipfriends

`ADMIN => NO SE USA`
```php
$app->post('/import_devices', \App\Controllers\DeviceController::class . ':importerDevices');
```
formato:
```
fullname,ringsecs,accountcode,phonetype,username,secret,nat,monitor,record,tenantid,callerid,phone
Greg Cullup,10,,softphone,208,1234,"force_rport,comedia",0,none,25,Greg Cullup <4085142618>,4085142618
Greg Hatch,10,,softphone,222,1234,"force_rport,comedia",0,none,25,Greg Hatch <4085142618>,4085142618
Newark Alarm,10,,softphone,241,1234,"force_rport,comedia",0,none,25,Newark Alarm <4085142618>,4085142618
Greg Hatch WFH,10,,softphone,434,1234,"force_rport,comedia",0,none,25,Greg Hatch WFH <4085142618>,4085142618
```

`ADMIN => ` Exportacion de phones, se lo realiza desde el screen Numbers
```php
$app->post('/import_phones', \App\Controllers\PhoneController::class . ':importerPhones');
```
formato
```
phone,ptypeID,description,taken,tenantid,active,calls,prefix
"62789465132",1,"test","n",26,0,5,"001"
```

Exporta la tabla phones con todos sus campos en formato csv espeficicandoses sus id (esta hecha para escoger los phones desde el admin)

`ADMIN => ` en el screeen `Numbers` al seleccionar los checks box en cada fila de los phones, aparece la opcion `Export` el resultado se exporta a un archivo csv.
```php
$app->post('/export_phones', \App\Controllers\PhoneController::class . ':exportPhones');
```
parametro de entrada
```json
{
	"id": "23|56|67|98"
}
```

Importa phones desde un file 

`ADMIN => ` en el screeen `Numbers` la opcion `Import`, Campos: FIle, description, type VIRTUAL/PSTN, Caller ID group.
```php
$app->post('/import_dni', \App\Controllers\PhoneController::class . ':importerOwnPhones');
```
parametros de entrada
```js
data = {
  tenantid: tenantid, 
  filename: $('#file').val(),
  type: $('#ptypeID').val(),
  desc: $('#description').val(),
  groupid: $('#calleridgroupid option:selected').val(),
  csv: encodeBase64(filecontent)
};
```
formato
```
PHONENUMBER|DID
7285858585 
7285858586 
7285858587
```

Importa supress phones

`ADMIN => YA NO SE USA`

```php
$app->post('/suppress_phones', \App\Controllers\PhoneController::class . ':suppressionPhone');
```
parametros de entrada
```js
params = {
	camp_id: camp_id, 
	poolid: poolid, 
	userid: "{{ auth.user.userid }}", 
	filename: filename,
	csv: encodeBase64(filecontent)
};
```

# NEW AUTH 

Realiza el primer paso de autenticacion entregando los minimos datos necesarios (no requiere token)

`ADMIN =>  Se envía al api usuario, contraseña y usertype (admin no envia este parametro), se espera devuelva la lista de tenants y usertypes de cada tenant que tiene el usuario asignado. En el caso de admin solo se envía usuario y contraseña ya que determinar un usertype no se puede. La lógica de api es si viene vacio selecciona todos los usertype excepto 27 30.`

`Casos:`

`Vacío: Respuesta vacía, presenta mensaje de que no tiene tenants asignados.`
`Uno: Si tiene un solo tenant envía a /authuser el email, password y userid. y devuelve los datos completos del usuario`
`Varios: Si tiene varios tenants se procede a presentar una pantalla donde seleccione el tenant y el usertype que requiere y cuando se selecciona se envia a /authuser el email, password y userid.`
`La lista de tenants y usertypes se guarda en variable de session "cookie/sessionStorage" ya que esta lista sirve para hacer tenant swap. Cuando se selecciona un tenant y usertype se corre la ruta /authuser`

```php
$app->post('/authlogin', \App\Controllers\UserController::class . ':getAuthLogin');
```
Como el chequeo es por email si se detecta que un passwd esta en blanco asume que el user no esta en Cognito y lo crea
```json
parametros de entrada
{
   "email": "jsainz@callevo.com",
   "password": "s6P7v4K1",
   "usertype" : 1
}
```
resultado
```json
{
    "status": "ok",
    "message": [
        {
            "username": "jjscadmin",
            "pass": "s6P7v4K1",
            "email": "jsainz@callevo.com",
            "userid": "3",
            "tenantid": "25",
            "usertype": "1",
            "usertype_description": "System Administrator",
            "tenant_name": "Default Tenant",
            "aws_websocket": "fcmjso36b7.execute-api.us-east-1.amazonaws.com",
            "region": "us-east-1"
        },
        {
            "username": "u8629ac802ff357b97fc",
            "pass": "s6P7v4K1",
            "email": "jsainz@callevo.com",
            "userid": "381",
            "tenantid": "86",
            "usertype": "1",
            "usertype_description": "System Administrator",
            "tenant_name": "Tenant Rick",
            "aws_websocket": "fcmjso36b7.execute-api.us-east-1.amazonaws.com",
            "region": "us-east-1"
        },
		.
	]
}	
```

Paso final del auth (no requiere token)

`ADMIN => ` De la lista presentada se selecciona un tenant y usertype y se envia al api devolviendo toda la infromacion del usuario.

```php
$app->post('/authuser', \App\Controllers\UserController::class . ':getAuthUser');
```
parametros de entrada
```json
{
   "email": "jsainz@callevo.com",
   "password": "s6P7v4K1",
   "userid" : 849
}
```
Necesita cual especificamente es el user a validar para devolver la informacion necesaria
```json
{
    "status": "ok",
    "message": {
        "username": "u25dc6742b1cf56bc0f5",
        "fullname": "JSainz Admin",
        "email": "jsainz@callevo.com",
        "userid": "849",
        "tenantid": "139",
        "usertype": "1",
        "hashed": "$2y$10$Y0PP69Id3g81aUyqLejHWOMPNzqZnCs2rip3nEsxLOSiLF7ARoLia",
        "agentid": "833",
        "agents_name": "JSainz Admin",
        "agent_code": "u25dc6742b1cf56bc0f5",
        "urllogin": "",
        "urlLogout": "",
        "urlbtwcalls": "https://grafana.callevo.net/d/b0a29dd1-9928-438d-8b3c-e94c88185e0c/btwcalls?orgId=1&kiosk&theme=light&var-agentid&var-campid",
        "homepage": "performance",
        "newhomepage": "2",
        "scopes": "read|write|delete",
        "usertype_description": "System Administrator",
        "statusagent": "0001|0001|0001|0001|0001",
        "limitexport": "0",
        "activate_tenant": "y",
        "integration_type": "0",
        "selectcmp": "1",
        "stand_alone_clicker": "1",
        "kamailio": "sip:kamailio.callevo.net:5060",
        "timeused": "999999.9999",
        "account_balance": "0.0000",
        "authdomain": "172.30.11.103",
        "tenant_name": "Mid West Cash Offer",
        "menu": [
            {
                "id": "1",
                "headertext": "home",
                "role_name": "main",
                "menu_order": "1",
                "permissions": "read",
                "sub_menu": [
                    {
                        "subid": "10",
                        "mainid": "1",
                        "name": "Home",
                        "submenu": "0",
                        "sub_role_name": "campaign",
                        "sub_menu_order": "1",
                        "sub_role_permissions": "read"
                    }
                ]
            },
             
            {
                "id": "4",
                "headertext": "dnc",
                "role_name": "dncs",
                "menu_order": "4",
                "permissions": "read,write,delete",
                "sub_menu": [
                    {
                        "subid": "23",
                        "mainid": "4",
                        "name": "DNC",
                        "submenu": "0",
                        "sub_role_name": "dncs",
                        "sub_menu_order": "1",
                        "sub_role_permissions": "read,write,delete"
                    },
                    {
                        "subid": "16",
                        "mainid": "4",
                        "name": "Supporting Data",
                        "submenu": "1",
                        "sub_role_name": "supporting",
                        "sub_menu_order": "6",
                        "sub_role_permissions": "read,write,delete",
                        "menu_items": [
                            {
                                "itemid": "36",
                                "parentid": "16",
                                "item_name": "VAN Api Key",
                                "item_role_name": "supporting",
                                "item_menu_order": "4",
                                "item_role_permissions": "read,write"
                            },
                            {
                                "itemid": "35",
                                "parentid": "16",
                                "item_name": "Recordings",
                                "item_role_name": "supporting",
                                "item_menu_order": "3",
                                "item_role_permissions": "read,write"
                            },
                            {
                                "itemid": "34",
                                "parentid": "16",
                                "item_name": "Key generator",
                                "item_role_name": "supporting",
                                "item_menu_order": "2",
                                "item_role_permissions": "read,write"
                            },
                            {
                                "itemid": "33",
                                "parentid": "16",
                                "item_name": "Timezone",
                                "item_role_name": "supporting",
                                "item_menu_order": "1",
                                "item_role_permissions": "read,write"
                            },
                            {
                                "itemid": "37",
                                "parentid": "16",
                                "item_name": "Webform",
                                "item_role_name": "supporting",
                                "item_menu_order": "5",
                                "item_role_permissions": "read,write,delete"
                            }
                        ]
                    }
                ]
            },
            
        ],
        "roles": [
            {
                "name": "rsalesviewer",
                "permissions": "read",
                "roles_order": "99",
                "admin_type": "1"
            },
            {
                "name": "ragentsviewer",
                "permissions": "read",
                "roles_order": "99",
                "admin_type": "1"
            },
            {
                "name": "rleadsviewer",
                "permissions": "read",
                "roles_order": "99",
                "admin_type": "1"
            },
            
        ],
        "aws_websocket": "fcmjso36b7.execute-api.us-east-1.amazonaws.com",
        "region": "us-east-1",
        "Token": "eyJraWQiOiJnVTVhMEUxUW95bGVtaFwvWE8xc3hjMHQ0NEFobXkzVktoUzZ0eGlPb080dz0iLCJhbGciOiJSUzI1NiJ9.eyJzdWIiOiI0MTNiMjgxYS0wZTU0LTQxYTEtYTM1Ni0xZWQ5ZGY1NGFlNTMiLCJlbWFpbF92ZXJpZmllZCI6dHJ1ZSwiaXNzIjoiaHR0cHM6XC9cL2NvZ25pdG8taWRwLnVzLWVhc3QtMS5hbWF6b25hd3MuY29tXC91cy1lYXN0LTFfN25INzZQQWFTIiwiY29nbml0bzp1c2VybmFtZSI6InUyNWRjNjc0MmIxY2Y1NmJjMGY1Iiwib3JpZ2luX2p0aSI6ImIyYzc3Y2MyLTEzZTMtNDQ5Yy1hYzU3LTIzNTVhNjRiZWM4ZSIsImF1ZCI6Ijc1N2UydnY1NXNsdW5oMDlyNTRqdTM1Z2U3IiwiZXZlbnRfaWQiOiIxMDNiZTM0Yi0yYzEyLTRjZTMtOWE2OS0xMTljYjcyZGZmODYiLCJ1cGRhdGVkX2F0IjoxNzA0Mzc5ODI1LCJ0b2tlbl91c2UiOiJpZCIsImF1dGhfdGltZSI6MTcyNzM4MDkyMSwibmFtZSI6IkpTYWlueiBBZG1pbiIsImV4cCI6MTcyNzQ2NzMyMSwiaWF0IjoxNzI3MzgwOTIxLCJqdGkiOiJkYTlkZGFmYy1hNjYyLTQ2NzAtYTRhZS1jYjk5OTkzMmQ1MDMiLCJlbWFpbCI6ImpzYWluekBjYWxsZXZvLmNvbSJ9.gKkJ9vRcYakzFmb1RJtquq5soDRtELQO4XnQ9_ccouWGZEz5JmEkakG4h3F8nR3rA3JFMbLxVXO-3uKJ7RV6jsvVHG105mVFDmM3Jrrkr6GsTj8sMEIiH4y0p6LISqECsK7sfGPkxK3Mz30W1_Y0MYeTA0hQLbitp7o3LH2Vt3oE50SqqngaNr0Ljv6oabLrJTcWrqgLZ2qHR8d5IdDrXPtdxAQPbSj05lszMQUyuJsK2ollghxluwhKqcbLBu_DIbqve0HpykiFrh-RIH73Rkw1w_-fhELOG1N9EDtlu4J380Et-fUwIiIAVw6dr_oZaKX_LjQjdglzsKRxLKG6PA",
        "createnewtoken": false
    }
}
```

Desloguea al user mediante un SP

`ADMIN =>` Envia informacion para cerrar la session del usuario

```php
$app->post('/logout', \App\Controllers\UserController::class . ':logout');
```
parametros de entrada
```json
{
    "email": "jsainz@callevo.com",
    "password": "s6P7v4K1",
    "userid": "845"
}
```
Hay una validacion importante y es que el user que esta desloguendose envia un token que sera vrificado con el que pertenece al userid y si todo esta correcto invoca al SP
`CALL AgentLogoff(:agent_code, :mdata)`


Cambia el passwd del user (no requiere token)

`ADMIN => ` Se envia email, newpassword, oldpassword, al realizar el cambio de password, retorna status OK y resirige a la pantalla de login.

```php
$app->post('/changepass', \App\Controllers\UserController::class . ':changePassword');
```
Parametros de entrada
```json
{
    "email": "dianek1205@comcast.net",
    "newPassword": "MURPhY!$",
    "oldPassword": "*8m8927I0-"
}
```
OBSERVACION el cambio se hace para todos los usernames que pertenezcan al mismo email.


Resetea el passwd

`ADMIN => ` En el screen de `Users` existe la opcion de seleccionar al usuario que necesita resetear la contraseña, y luegoi dar click sobre el boton `Reset` que ejecuta esta ruta.

```php
$app->post('/resetpass', \App\Controllers\UserController::class . ':resetPassword');
```
Borra todos los passwd de la base que pertenecen al mismo email y elimina los user del cognito
Esta funcion solo debe ser usadas por administradores

Parametros de entrada
```json
{
    "email":"aliciam@smw104.org"
}
```

Desbloquea un user que haya sido bloqueado por muchos intentos fallidos

`ADMIN =>  NO SE USA`
```php
$app->post('/unlock_user', \App\Controllers\UserController::class . ':unlockUser');
```
Realiza un conjunto de operaciones conservando los datos originales almacenados en la base de modo que no hay cambios en el passwd (actualiza los token)
parametros de entrada
```json
{
    "username":"u2174468eaa92aa261b6"
}
```

Establece un mecanismo de cambio de passwd con seguridades

`ADMIN =>  NO SE USA` en su lugar se utsa `confirm_change_password`

```php
$app->post('/forgot_password', \App\Controllers\UserController::class . ':forgotPassword');
```
Parametro de entrada
```json
{
    "email": "jsainz@callevo.com",
    "key": "9vOTdzF8rXWT7jHOm9Zf5V-pEckUGy9YuX6TFLfKeT2RJyuorC41j-C9y-BtwfV_nuVf20drEg780Ww9Hv_2"
}
```
Esta clave es generada desde las paginas del admin donde se pide el email para el envio de las instrucciones de cambio. 

Despues de la verificacion del key, se genera una clave temporal y se envia la misma al email de recuperacion, la clave temporal es configurada para todos los usernames que pertenecen al email.


# TEAMS / QUEUE_TABLE 

Ruta para PDI devuelve los teams de un tenantid (simplificado) (se toma del token)

`ADMIN => NO SE USA` Admin obtiene la informacion desde los modelos de admin

```php
$app->get('/teams[/p/{p}/f/{f}/o/{o}/i/{i}]', \App\Controllers\QueueTableController::class . ':listall')->setName('teams');
```
```json
[
	{
		"queueid": 471,
		"name": "q98b58e3f5ba22cb3023",
		"team_name": "hans_existing_customer",
		"strategy": "leastrecent",
		"created_at": "2021-12-15 15:48:34",
		"updated_at": "2022-01-06 21:19:35",
		"deleted_at": null
	},
	{
		"queueid": 472,
		"name": "q98d5aa59e09916771c5",
		"team_name": "hans_manual_dial",
		"strategy": "leastrecent",
		"created_at": "2021-12-15 15:48:42",
		"updated_at": "2022-01-07 18:42:48",
		"deleted_at": null
	},
	
]
```

Ruta para admin (todos los datos)

`ADMIN => NO SE USA`

```php
$app->get('/queues_table', \App\Controllers\QueueTableController::class . ':listall')->setName('queues_table');
```
```json
[
	{
		"queueid": 1005,
		"tenantid": "138",
		"name": "q1386e3a4a0156f23c96",
		"team_name": "jjsc_tenant_test_team",
		"musiconhold": "queues",
		"announce": "",
		"context": "internal",
		"timeout": "10",
		"monitor_format": "wav",
		"queue_youarenext": "queue-youarenext",
		"queue_thereare": "queue-thereare",
		"queue_callswaiting": "queue-callswaiting",
		"queue_holdtime": "queue-holdtime",
		"queue_minutes": "queue-minutes",
		"queue_seconds": "queue-seconds",
		"queue_lessthan": "queue-lessthan",
		"queue_thankyou": "queue-thankyou",
		"queue_reporthold": "queue-reporthold",
		"announce_frequency": "60",
		"announce_round_seconds": "0",
		"announce_holdtime": "no",
		"retry": "5",
		"wrapuptime": "0",
		"maxlen": "0",
		"servicelevel": "120",
		"strategy": "leastrecent",
		"joinempty": "yes",
		"leavewhenempty": "no",
		"eventmemberstatus": "1",
		"eventwhencalled": "1",
		"reportholdtime": "0",
		"memberdelay": "0",
		"weight": "100",
		"timeoutrestart": "0",
		"totalcalls": "0",
		"completed": "0",
		"dropped": "0",
		"abandoned": "0",
		"callscompletedinsl": "0",
		"current": "0",
		"onhold": "0",
		"mincallleng": "0.00",
		"maxcallleng": "0.00",
		"minwaiting": "0.00",
		"maxwaiting": "0.00",
		"mintalktime": "0.00",
		"maxtalktime": "0.00",
		"monitor_type": "mixmonitor",
		"autofill": "1",
		"setinterfacevar": "1",
		"ringinuse": "0",
		"internal": "n",
		"announce_position": "n",
		"autopause": "0",
		"monitor_join": "0",
		"defaultrule": "cmprule",
		"teamcloser": "0",
		"closingfor": "0",
		"announceposition": "0",
		"announceholdtime": "0",
		"autodisptime": "10",
		"supervisorteam": "0",
		"ignorebusy": "0",
		"autopausebusy": "0",
		"created_at": "2022-10-20 14:07:20",
		"updated_at": "2023-07-06 03:44:32",
		"deleted_at": null,
		"queue_member_table": [
			{
				"memberid": 13339,
				"queueid": "1005",
				"uniqueid": "0",
				"queue_name": "q1386e3a4a0156f23c96",
				"agentid": "829",
				"interface": "Agent\/u2570aafa7dc99cbd7c8",
				"penalty": "0",
				"callstaken": "0",
				"status": "LOGOFF",
				"lastcall": "0",
				"paused": "0",
				"manager": "n",
				"membername": "",
				"calls": "0",
				"announce_holdtime": "no",
				"wrapuptime": "0",
				"camp_id": "0",
				"lead_id": "0",
				"callid": "0",
				"channelid": "",
				"created_at": "2023-02-27 17:18:36",
				"updated_at": "2023-02-27 17:18:36",
				"deleted_at": null
			},
		]
	},
	
}	
```

	
Ruta para PDi Devuelve un team por su nombre (queue_table)

`ADMIN => NO SE USA`
```php
$app->get('/team[/{code}]', \App\Controllers\QueueTableController::class . ':getQueueTable');
```
```json
[
	{
		"queueid": 471,
		"name": "q98b58e3f5ba22cb3023",
		"team_name": "hans_existing_customer",
		"strategy": "leastrecent",
		"created_at": "2021-12-15 15:48:34",
		"updated_at": "2022-01-06 21:19:35",
		"deleted_at": null
	}
]
```


Ruta para PDI

`ADMIN => NO SE USA`
```php
$app->get('/team_members/{queueid}[/p/{p}/f/{f}/o/{o}/i/{i}]', \App\Controllers\QueueTableController::class . ':getQueueMembers');
```
```json
[
	{
		"memberid": "83781",
		"userid": "1481",
		"username": "u139c69cf1f6827d0879",
		"fullname": "JSainz Agent",
		"email": "jsainz@callevo.com"
	},
	{
		"memberid": "83785",
		"userid": "1480",
		"username": "u13979200410e6931fc6",
		"fullname": "ricktestagent",
		"email": "rmorris@callevo.com"
	},
	{
		"memberid": "83787",
		"userid": "1459",
		"username": "u13913ceac3f4a263218",
		"fullname": "Saul Diaz",
		"email": "sdiaz@callevo.com"
	},
	{
		"memberid": "83789",
		"userid": "894",
		"username": "u139533badbf98ba6373",
		"fullname": "SBorja Agent",
		"email": "santiago@callevo.com"
	}
]
```

Crea un team 

`ADMIN => NO SE USA`
```php
$app->post('/team', \App\Controllers\QueueTableController::class . ':modifyQueueTable');
$app->put('/team/{id}', \App\Controllers\QueueTableController::class . ':modifyQueueTable');
```
```json
{
	"queueid": "-1",
	"record": {
		"team_name": "PDI Test Team",
		"announce_holdtime": "no",
		"servicelevel": "60"
	}
}
```

Borra el team por id

`ADMIN => NO SE USA`

```php
$app->delete('/team/{id}', \App\Controllers\QueueTableController::class . ':deleteQueueTable');
```

Inserta en el queue_member_table, busca los datos del queue_table por el queueid

`ADMIN => NO SE USA`

```php
$app->post('/team_member', \App\Controllers\QueueTableController::class . ':modifyQueueMember');
```
```json
{
   "queueid": 313,
   "userid" : 2312312,
}   
```

Borra el team member por id

`ADMIN => NO SE USA`

```php
$app->delete('/team_member/{memberid}', \App\Controllers\QueueTableController::class . ':deleteQueueMember');
```


`ADMIN => NO SE USA`

```php
$app->get('/agent_teams_closingfor/{agentid}', \App\Controllers\QueueTableController::class . ':getTeamClosingfor');
{
	"status": "ok",
	"message": [
		{
			"queueid": 111,
			"name": "sdfsfsdfs"
			"team_name": "sdsdfadsafsd"
		},
	]
}
```

`ADMIN => NO SE USA` el admin lo toma de los modelos de admin.

```php
$app->get('/queue_table/{id}', \App\Controllers\QueueTableController::class . ':getQueueTable');
```


Adiciona modifca un queue_table y sus miembros

`ADMIN => ` En el screen `team edit`

```php
$app->post('/queue_table', \App\Controllers\QueueTableController::class . ':modifyQueueTable');
$app->put('/queue_table', \App\Controllers\QueueTableController::class . ':modifyQueueTable');
```
```js
{
    queueid: $('#queueid').val(),
    record: { 
		name: $('#name').val(),
		team_name: $('#team_name').val().toLowerCase(),
		camp_id: $('#camp_id').val(),
		strategy: $('#strategy option:selected').val(),
		maxlen: $('#maxlen option:selected').val(),
		retry: 2,
		announce_frequency: $('#announce_frequency option:selected').val(),
		wrapuptime: $('#wrapuptime option:selected').val(),
		autodisptime: $('#autodisptime option:selected').val(),
		musiconhold: "queues",
		announce_position: ($('#announce_position').is(':checked') ? 'y' : 'n'),
		announce_holdtime: $('#announce_holdtime option:selected').val(),
		servicelevel: $('#servicelevel option:selected').val(),
		supervisorteam: $('#supervisorteam option:selected').val(),
		closingfor: $('#closingfor option:selected').val(),
		autofill: ($('#autofill').is(':checked') ? '1' : '0'),
		autopause: ($('#autopause').is(':checked') ? '1' : '0'),
		ignorebusy: ($('#ignorebusy').is(':checked') ? '1' : '0'),
		autopausebusy: ($('#autopausebusy').is(':checked') ? '1' : '0'),
		internal: 'n',
		},
	}
    queue_member_table: [
		{
            agentid: $(this).val(),    
            queue_name:  $('#name').val().toLowerCase(),
            interface: 'Agent/'.concat($(this).data('agentcode')),
        },
		.
	],
}	
```

Borra el team (queue_table) por id

`ADMIN => ` Elimina un team desde el screen de teams 

```php
$app->delete('/queue_table/{id}', \App\Controllers\QueueTableController::class . ':deleteQueueTable');
```

# TIMEZONE / GROUPTZ 

Recupera los timezones o uno por id

`ADMIN => NO SE USA` Los datos se toman de los modelos del admin

```php
$app->get('/timezones[/p/{p}/f/{f}/o/{o}/i/{i}]', \App\Controllers\TimeZoneController::class . ':listall')->setName('timezones');
$app->get('/timezone/{id}', \App\Controllers\TimeZoneController::class . ':getTime');
```
```json
[
	{
		"timeid": 304,
		"tenantid": "98",
		"name": "MST",
		"comment": "Mountain Time Zone",
		"h00": "N",
		"h0": "n",
		"h01": "N",
		"h02": "N",
		"h03": "N",
		"h04": "N",
		"h05": "N",
		"h06": "N",
		"h07": "N",
		"h08": "Y",
		"h09": "Y",
		"h10": "Y",
		"h11": "Y",
		"h12": "Y",
		"h13": "Y",
		"h14": "Y",
		"h15": "Y",
		"h16": "Y",
		"h17": "Y",
		"h18": "Y",
		"h19": "N",
		"h20": "N",
		"h21": "N",
		"h22": "N",
		"h23": "N",
		"offset": "7",
		"systemtzid": "94",
		"sla": "0"
	},
	{
		"timeid": 453,
		"tenantid": "98",
		"name": "AZT",
		"comment": "Arizona TZ",
		"h00": "N",
		"h0": "n",
		"h01": "N",
		"h02": "N",
		"h03": "N",
		"h04": "N",
		"h05": "N",
		"h06": "N",
		"h07": "N",
		"h08": "Y",
		"h09": "Y",
		"h10": "Y",
		"h11": "Y",
		"h12": "Y",
		"h13": "Y",
		"h14": "Y",
		"h15": "Y",
		"h16": "Y",
		"h17": "Y",
		"h18": "Y",
		"h19": "N",
		"h20": "N",
		"h21": "N",
		"h22": "N",
		"h23": "N",
		"offset": "7",
		"systemtzid": "95",
		"sla": "1"
	},
	
]	
```

Agrega/modifica timezone tomando el id del token

`ADMIN => ` Guarda la informacion editada de un timezone

```php
$app->post('/timezone', \App\Controllers\TimeZoneController::class . ':modifyTimezone');
$app->put('/timezone', \App\Controllers\TimeZoneController::class . ':modifyTimezone');
```
```js
{
  timeid:$("#timeid").val(),
  name:$("#name").val(),
  comment:$("#comment").val(),
  h00:($("#h00").is(":checked") ? 'Y': 'N') ,
  h01:($("#h01").is(":checked") ? 'Y': 'N') ,
  h02:($("#h02").is(":checked") ? 'Y': 'N') ,
  h03:($("#h03").is(":checked") ? 'Y': 'N') ,
  h04:($("#h04").is(":checked") ? 'Y': 'N') ,
  h05:($("#h05").is(":checked") ? 'Y': 'N') ,
  h06:($("#h06").is(":checked") ? 'Y': 'N') ,
  h07:($("#h07").is(":checked") ? 'Y': 'N') ,
  h08:($("#h08").is(":checked") ? 'Y': 'N') ,
  h09:($("#h09").is(":checked") ? 'Y': 'N') ,
  h10:($("#h10").is(":checked") ? 'Y': 'N') ,
  h11:($("#h11").is(":checked") ? 'Y': 'N') ,
  h12:($("#h12").is(":checked") ? 'Y': 'N') ,
  h13:($("#h13").is(":checked") ? 'Y': 'N') ,
  h14:($("#h14").is(":checked") ? 'Y': 'N') ,
  h15:($("#h15").is(":checked") ? 'Y': 'N') ,
  h16:($("#h16").is(":checked") ? 'Y': 'N') ,
  h17:($("#h17").is(":checked") ? 'Y': 'N') ,
  h18:($("#h18").is(":checked") ? 'Y': 'N') ,
  h19:($("#h19").is(":checked") ? 'Y': 'N') ,
  h20:($("#h20").is(":checked") ? 'Y': 'N') ,
  h21:($("#h21").is(":checked") ? 'Y': 'N') ,
  h22:($("#h22").is(":checked") ? 'Y': 'N') ,
  h23:($("#h23").is(":checked") ? 'Y': 'N') ,
}
```

Igual al anterior pero para el tenantid especificado

`ADMIN => NO SE USA `
```php
$app->post('/timezones/{tenantid}', \App\Controllers\TimeZoneController::class . ':createTz');
```


Borra un timezone por ID

`ADMIN => ` En el screen timezone, luego de dar click sobre la fila a eliminar se activara el boton eliminar para el proceso respectivo.

```php
$app->delete('/timezone/{id}', \App\Controllers\TimeZoneController::class . ':deleteTimezone');
```

# GROUPTZ 

Devuelve los groputz por tenantid especificado

`ADMIN => NO SE USA` opcion quedo desactualizada y no se usa.

```php
$app->get('/grouptzs', \App\Controllers\GrouptzController::class . ':listall')->setName('grouptzs');
```
parametro de entrada
```json
{
	"tenantid" : 138
}
```
```json
resultado
[
	{
		"timegid": "2203",
		"timeid": "613",
		"camp_id": "425",
		"h00": "N",
		"h0": "n",
		"h01": "N",
		"h02": "N",
		"h03": "N",
		"h04": "N",
		"h05": "N",
		"h06": "N",
		"h07": "Y",
		"h08": "Y",
		"h09": "Y",
		"h10": "Y",
		"h11": "Y",
		"h12": "Y",
		"h13": "Y",
		"h14": "Y",
		"h15": "Y",
		"h16": "Y",
		"h17": "Y",
		"h18": "Y",
		"h19": "N",
		"h20": "N",
		"h21": "N",
		"h22": "N",
		"h23": "N",
		"offset": "5",
		"systemtzid": "49",
		"enabled": "1",
		"dls": "1"
	},
	{
		"timegid": "2204",
		"timeid": "614",
		"camp_id": "425",
		"h00": "N",
		"h0": "n",
		"h01": "N",
		"h02": "N",
		"h03": "N",
		"h04": "N",
		"h05": "N",
		"h06": "Y",
		"h07": "Y",
		"h08": "Y",
		"h09": "Y",
		"h10": "Y",
		"h11": "Y",
		"h12": "Y",
		"h13": "Y",
		"h14": "Y",
		"h15": "Y",
		"h16": "Y",
		"h17": "N",
		"h18": "N",
		"h19": "N",
		"h20": "N",
		"h21": "N",
		"h22": "N",
		"h23": "N",
		"offset": "7",
		"systemtzid": "52",
		"enabled": "1",
		"dls": "1"
	},
	
]	
```

Recupera el grouptz con sus relaciones

`ADMIN => NO SE USA`

```php
$app->get('/grouptz/{id}', \App\Controllers\GrouptzController::class . ':getGrouptz');
```
```json
[
	{
		"timegid": 2203,
		"timeid": "613",
		"camp_id": "425",
		"h00": "N",
		"h0": "n",
		"h01": "N",
		"h02": "N",
		"h03": "N",
		"h04": "N",
		"h05": "N",
		"h06": "N",
		"h07": "Y",
		"h08": "Y",
		"h09": "Y",
		"h10": "Y",
		"h11": "Y",
		"h12": "Y",
		"h13": "Y",
		"h14": "Y",
		"h15": "Y",
		"h16": "Y",
		"h17": "Y",
		"h18": "Y",
		"h19": "N",
		"h20": "N",
		"h21": "N",
		"h22": "N",
		"h23": "N",
		"offset": "5",
		"systemtzid": "49",
		"enabled": "1",
		"dls": "1",
		"campaign": {
			"camp_id": 425,
			"camp_name": "camp-name-cl",
			"trunkID": "3",
			"camp_channels": "0",
			"ivrid": "0",
			"amdivrid": "0",
			"phoneID": "0",
			"tenantid": "138",
			"groupid": "162",
			"camp_description": "",
			"active": "y",
			"started": "00:00:00",
			"camp_type": "CL",
			"ratio": "3:1",
			"status": "0",
			"inbound_number": "_cmp425$$",
			"queue_name": "q1386e3a4a0156f23c96",
			"maxretrys": "9999",
			"waittime": "50",
			"callerid": "32423424234",
			"busyretrytime": "7200",
			"amdretrytime": "14400",
			"startdialing": "00:00:00",
			"stopdialing": "00:00:00",
			"afterhourroute": "",
			"busycb": "y",
			"amdCB": "y",
			"noanswercb": "y",
			"noansretrytime": "28800",
			"timezones": "n",
			"invalidcb": "y",
			"invalidretrytime": "28800",
			"urlcall": "https:\/\/remotep.callevo.net\/aws_survey?id=11",
			"prepend": "1",
			"strip": "0",
			"dropcb": "y",
			"droptime": "14400",
			"customfield": "custom",
			"customlabel": "",
			"notifychannel": "",
			"notifytime": "30",
			"showcustomfield": "n",
			"notifyholding": "n",
			"forcedisposition": "n",
			"showdisp": "n",
			"defaultdisp": "0",
			"adaptive_dl_diff_target": "0",
			"adaptive_intensity": "4.00",
			"drop_limit": "3",
			"allow_inbound": "n",
			"agentcmp": "0",
			"calldataS": "<p><strong>Name {lead_fname} {lead_mname} {lead_lname}<\/strong><\/p>",
			"calldataF": "",
			"callDataN": "",
			"inlinecallid": "y",
			"useautostart": "n",
			"buildrange": "",
			"minconnrate": "90",
			"demo": "0",
			"demoduration": "30",
			"democonnrate": "8",
			"fetcherwaittime": "1000",
			"brokenCB": "4",
			"linesdialed": "0",
			"talktime_alarm": "30",
			"talktime_color": "7382763",
			"timenoready": "20",
			"timenoready_color": "15536915",
			"timebreak": "30",
			"timebreak_color": "15887894",
			"timelunch": "30",
			"timelunch_color": "15780361",
			"timewrap": "15",
			"timewrap_color": "3407749",
			"goals": "0",
			"goalstype": "1",
			"expectedwaittime": "25",
			"waitingtime_alarm": "30",
			"waittime_color": "2208526",
			"detectmachine": "0",
			"initialrecordID": "0",
			"finalrecordID": "0",
			"agentammmessage": "0",
			"agentofflinemessage": "0",
			"pressonekey": "1",
			"linked_campaign": "0",
			"brokencallback": "4",
			"customquotes": "0",
			"recordcalls": "n",
			"tzscrubid": "3",
			"pepperclient": "callbacks",
			"sqlfilter": "AND custom9 != ''",
			"timeother": "0",
			"timeother_color": "0",
			"timebathroom": "0",
			"timebathroom_color": "0",
			"timemeeting": "0",
			"timemeeting_color": "0",
			"ordertype": "2",
			"didrotation": "1",
			"smsnumber": "",
			"posturlcall": "",
			"qcenabled": "y",
			"usedncglobal": "n",
			"usecmpdnc": "y",
			"usecampdncfrom": "y",
			"calltimeid": "99",
			"qcurl": "",
			"integration_type": "0",
			"two_way_integration": "0",
			"activist_codes": "",
			"van_type": "0",
			"multinumber": "0",
			"alternate_numbers": "0",
			"recordings": "1",
			"sla": "60",
			"created_at": "2022-10-20 14:08:08",
			"updated_at": "2024-09-27 16:10:31",
			"deleted_at": null,
			"cps": "0",
			"logo": "HC1LNM_logo_Image_2021-01-03_at_5.20.50_PM",
			"logotype": "jpeg",
			"agentmessage": null,
			"show_alert": "7",
			"amdtransfer": "",
			"simulated": "0",
			"waitingrecordID": "0"
		},
		"time_zone": {
			"timeid": 613,
			"tenantid": "138",
			"name": "CST",
			"comment": "Central Time Zone",
			"h00": "N",
			"h0": "n",
			"h01": "N",
			"h02": "N",
			"h03": "N",
			"h04": "N",
			"h05": "N",
			"h06": "N",
			"h07": "N",
			"h08": "Y",
			"h09": "Y",
			"h10": "Y",
			"h11": "Y",
			"h12": "Y",
			"h13": "Y",
			"h14": "Y",
			"h15": "Y",
			"h16": "Y",
			"h17": "Y",
			"h18": "Y",
			"h19": "N",
			"h20": "N",
			"h21": "N",
			"h22": "N",
			"h23": "N",
			"offset": "5",
			"systemtzid": "49",
			"sla": "1"
		}
	}
]
```

Agrega/modifica un grouptz

`ADMIN => OPCION DEPRECADA YA NO SE USA` y los datos los obtenia de los modelos de admin

```php
$app->post('/grouptz', \App\Controllers\GrouptzController::class . ':modifyGrouptz');
$app->put('/grouptz', \App\Controllers\GrouptzController::class . ':modifyGrouptz');
```
```js
$record = [
		'camp_id' => $data['camp_id'],
		'timeid' => $data['timeid'],
		'h00' => (empty($data['h00']) ? 'N' : $data['h00'] ),	
		'h01' => (empty($data['h01']) ? 'N' : $data['h01'] ),		
		'h02' => (empty($data['h02']) ? 'N' : $data['h02'] ),		
		'h03' => (empty($data['h03']) ? 'N' : $data['h03'] ),		
		'h04' => (empty($data['h04']) ? 'N' : $data['h04'] ),		
		'h05' => (empty($data['h05']) ? 'N' : $data['h05'] ),		
		'h06' => (empty($data['h06']) ? 'N' : $data['h06'] ),		
		'h07' => (empty($data['h07']) ? 'N' : $data['h07'] ),		
		'h08' => (empty($data['h08']) ? 'N' : $data['h08'] ),		
		'h09' => (empty($data['h09']) ? 'N' : $data['h09'] ),		
		'h10' => (empty($data['h10']) ? 'N' : $data['h10'] ),		
		'h11' => (empty($data['h11']) ? 'N' : $data['h11'] ),		
		'h12' => (empty($data['h12']) ? 'N' : $data['h12'] ),		
		'h13' => (empty($data['h13']) ? 'N' : $data['h13'] ),		
		'h14' => (empty($data['h14']) ? 'N' : $data['h14'] ),		
		'h15' => (empty($data['h15']) ? 'N' : $data['h15'] ),		
		'h16' => (empty($data['h16']) ? 'N' : $data['h16'] ),		
		'h17' => (empty($data['h17']) ? 'N' : $data['h17'] ),		
		'h18' => (empty($data['h18']) ? 'N' : $data['h18'] ),		
		'h19' => (empty($data['h19']) ? 'N' : $data['h19'] ),		
		'h20' => (empty($data['h20']) ? 'N' : $data['h20'] ),		
		'h21' => (empty($data['h21']) ? 'N' : $data['h21'] ),		
		'h22' => (empty($data['h22']) ? 'N' : $data['h22'] ),		
		'h23' => (empty($data['h23']) ? 'N' : $data['h23'] ),
		'offset' => $data["offset"],
];
```

Agrega grouptz para una camp_id

`ADMIN => OPCION DEPRECADA NO SE USA`

```php
$app->post('/grouptz/{camp_id}', \App\Controllers\GrouptzController::class . ':createGrouptz');
```


Borra un grouptz por id

`ADMIN => OPCION DEPRECADA NO SE USA`

```php
$app->delete('/grouptz/delete[/{id}]', \App\Controllers\GrouptzController::class . ':deleteGrouptz');
```

# USERS 

Devuelve lista de users con sus relaciones

`ADMIN => NO SE USA`

```php
$app->get('/users[/p/{p}/f/{f}/o/{o}/i/{i}]', \App\Controllers\UserController::class . ':index');
```
```js
{
		"userid": 1985,
		"tenantid": "138",
		"usertype": "27",
		"username": "u13859bef7e3a9d52da9",
		"pass": "scor6pio0EN",
		"language": "en",
		"fullname": "Saul Diaz Agent",
		"email_verified": "1",
		"email": "sdiaz@callevo.com",
		"logged": "n",
		"stamp": "2023-04-20 01:05:29",
		"clientaccess": "0",
		"maxchannels": "200",
		"hashed": "$2y$10$R3W21w.\/5G5CjOaXrelqQu.gidIQpX3t.zrO1JzEPGGJ5iZKArwYK",
		"created_at": "2023-04-19T12:22:05.000000Z",
		"updated_at": "2023-04-20T01:05:29.000000Z",
		"deleted_at": null,
		"lastlogin": "2023-04-19 07:43:26",
		"Token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzUxMiJ9.eyJ0ZW5hbnRpZCI6IjEzOCIsInVzZXJpZCI6MTk4NSwidXNlcnR5cGUiOiIyNyIsInNjb3BlIjpbInJlYWQiXSwiZXhwaXJlIjoxNjk1MzA5ODY0LCJpYXQiOjE2OTUzMDYyNjR9.46jxFFszVHYQWYA80HPPvkelIlEQmWOeXRzA9J7SLVssNIbF3R7hCze3k4eAVqHhmWIeJh0u3S41x31t0HsO3A",
		"Teams": [
			{
				"memberid": 14898,
				"queueid": "1006",
				"uniqueid": "0",
				"queue_name": "q138c7d347f1fdbf320e",
				"agentid": "1969",
				"interface": "Agent\/u13859bef7e3a9d52da9",
				"penalty": "0",
				"callstaken": "0",
				"status": "LOGOFF",
				"lastcall": "0",
				"paused": "0",
				"manager": "n",
				"membername": "",
				"calls": "0",
				"announce_holdtime": "no",
				"wrapuptime": "0",
				"camp_id": "0",
				"lead_id": "0",
				"callid": "0",
				"channelid": "",
				"created_at": "2023-04-19 12:22:06",
				"updated_at": "2023-04-19 12:22:06",
				"deleted_at": null
			},
			
		],
		"agent": {
			"agentid": 1969,
			"onHold": "0",
			"agent_code": "u13859bef7e3a9d52da9",
			"name": "Saul Diaz Agent",
			"autologoff": "15",
			"ackcall": "no",
			"wrapuptime": "0",
			"musiconhold": "agents",
			"updatecdr": "yes",
			"group": "",
			"recordagentcalls": "",
			"recordformat": "wav",
			"createlink": "yes",
			"urlprefix": "",
			"savecallsin": "",
			"custom_beep": "beep",
			"status": "LOGOFF",
			"statustime1": "2023-04-19 12:22:06",
			"tenantid": "138",
			"queue_name": "",
			"uniqueid": "0",
			"call_uniqueid": "",
			"loginstart": "0",
			"lastcall": "0",
			"paused": "0",
			"lasttime": null,
			"callid": "0",
			"loginunique": "",
			"holdchannel": "",
			"urllogin": "",
			"logintype": "GET",
			"urllogout": "",
			"logouttype": "GET",
			"urlbtwcalls": "",
			"btwcallstype": "GET",
			"gotoready": "n",
			"userid": "1985",
			"_ROLES": "",
			"token": "",
			"callswaiting": "0",
			"clientversion": "",
			"latency": "0",
			"sqldelay": "0",
			"selectleaddelay": "0",
			"uuid": "",
			"agent_message": "",
			"deleted_at": null,
			"created_at": null,
			"updated_at": null,
			"Password": "scor6pio0EN"
		},
		"user_type": {
			"usertype": 27,
			"descripcion": "Agent",
			"newhomepage": "0",
			"homepage": "none",
			"can_create": "0",
			"scopes": "read",
			"showinadmin": "0",
			"created_at": "2018-08-03T05:05:47.000000Z",
			"updated_at": "2023-02-27T18:20:11.000000Z",
			"deleted_at": null,
			"roles": []
		}
	},
	{
		"userid": 1989,
		"tenantid": "138",
		"usertype": "27",
		"username": "u1386d4e53b7dba5eb88",
		"pass": "s6P7v4K1",
		"language": "en",
		"fullname": "agent 2 test",
		"email_verified": "1",
		"email": "agent2test@callevo.com",
		"logged": "n",
		"stamp": "2023-04-19 22:42:35",
		"clientaccess": "0",
		"maxchannels": "200",
		"hashed": "$2y$10$H6bu7bz6HcgPi6VhWUe.q.6Cw2XZFoa6tmMApIU0ci6qhM\/iX4ThW",
		"created_at": "2023-04-19T22:20:09.000000Z",
		"updated_at": "2023-04-19T22:42:35.000000Z",
		"deleted_at": null,
		"lastlogin": null,
		"Token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzUxMiJ9.eyJ0ZW5hbnRpZCI6IjEzOCIsInVzZXJpZCI6MTk4OSwidXNlcnR5cGUiOiIyNyIsInNjb3BlIjpbInJlYWQiXSwiZXhwaXJlIjoxNjk1MzA5ODY0LCJpYXQiOjE2OTUzMDYyNjR9.n06Tyyj7CBfMonPG-QC0DHYMB5F8QETzi4kFn1V2SI6U271mHtub9LRSS_5dOzXEbmAlGckpguMboSEtZ13qGw",
		"Teams": [
			{
				"memberid": 14911,
				"queueid": "1006",
				"uniqueid": "0",
				"queue_name": "q138c7d347f1fdbf320e",
				"agentid": "1973",
				"interface": "Agent\/u1386d4e53b7dba5eb88",
				"penalty": "0",
				"callstaken": "0",
				"status": "LOGOFF",
				"lastcall": "0",
				"paused": "0",
				"manager": "n",
				"membername": "",
				"calls": "0",
				"announce_holdtime": "no",
				"wrapuptime": "0",
				"camp_id": "0",
				"lead_id": "0",
				"callid": "0",
				"channelid": "",
				"created_at": "2023-04-19 22:20:10",
				"updated_at": "2023-04-19 22:20:10",
				"deleted_at": null
			},
		
		],
		"agent": {
			"agentid": 1973,
			"onHold": "0",
			"agent_code": "u1386d4e53b7dba5eb88",
			"name": "agent 2 test",
			"autologoff": "15",
			"ackcall": "no",
			"wrapuptime": "0",
			"musiconhold": "agents",
			"updatecdr": "yes",
			"group": "",
			"recordagentcalls": "",
			"recordformat": "wav",
			"createlink": "yes",
			"urlprefix": "",
			"savecallsin": "",
			"custom_beep": "beep",
			"status": "LOGOFF",
			"statustime1": "2023-04-19 22:20:10",
			"tenantid": "138",
			"queue_name": "",
			"uniqueid": "0",
			"call_uniqueid": "",
			"loginstart": "0",
			"lastcall": "0",
			"paused": "0",
			"lasttime": null,
			"callid": "0",
			"loginunique": "",
			"holdchannel": "",
			"urllogin": "",
			"logintype": "GET",
			"urllogout": "",
			"logouttype": "GET",
			"urlbtwcalls": "",
			"btwcallstype": "GET",
			"gotoready": "n",
			"userid": "1989",
			"_ROLES": "",
			"token": "",
			"callswaiting": "0",
			"clientversion": "",
			"latency": "0",
			"sqldelay": "0",
			"selectleaddelay": "0",
			"uuid": "",
			"agent_message": "",
			"deleted_at": null,
			"created_at": null,
			"updated_at": null,
			"Password": "*UNUSED*"
		},
		"user_type": {
			"usertype": 27,
			"descripcion": "Agent",
			"newhomepage": "0",
			"homepage": "none",
			"can_create": "0",
			"scopes": "read",
			"showinadmin": "0",
			"created_at": "2018-08-03T05:05:47.000000Z",
			"updated_at": "2023-02-27T18:20:11.000000Z",
			"deleted_at": null,
			"roles": []
		}
	},
]	
```

Devuelve contadores de usuarios

`ADMIN => NO SE USA`

```php
$app->get('/users/count', \App\Controllers\UserController::class . ':index');
```
```json
{
	"total": 30,
	"ready": 0,
	"notready": 0,
	"others": 0
}
```

Devuelve user especificado por id con sus relaciones

`ADMIN => NO SE USA ` El admin lo captura desde el modelo 

```php
$app->get('/user/{userid}', \App\Controllers\UserController::class . ':getuser');
```
```json
[
	{
		"userid": 844,
		"tenantid": "138",
		"usertype": "27",
		"username": "u251521119c5bf9249ca",
		"pass": "s6P7v4K1",
		"language": "en",
		"fullname": "JJSc tenant test agent",
		"email_verified": "1",
		"email": "jsainz@callevo.com",
		"logged": "n",
		"stamp": "2024-09-30 09:57:03",
		"clientaccess": "0",
		"phone_number": "",
		"maxchannels": "200",
		"hashed": "$2y$10$HGkst.WeaJjv\/s3k3sxhm.DbqrtnqhwiV0TqG005Up95fslil1tmq",
		"refresh_token": "eyJjdHkiOiJKV1QiLCJlbmMiOiJBMjU2R0NNIiwi",
		"created_at": "2022-10-19T20:33:40.000000Z",
		"updated_at": "2024-09-30T09:57:03.000000Z",
		"deleted_at": null,
		"idtoken": "eyJraWQiOiJnVTVhMEUxUW95bGVtaFwvWE8xc3hjMHQ0NE",
		"lastlogin": "2024-09-30 04:57:03",
		"Token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzUxMiJ9.eyJ0ZW5hbnR",
		"Teams": [
			{
				"memberid": 40067,
				"queueid": "1006",
				"uniqueid": "0",
				"queue_name": "q138c7d347f1fdbf320e",
				"agentid": "828",
				"interface": "Agent\/u251521119c5bf9249ca",
				"penalty": "0",
				"callstaken": "0",
				"status": "LOGOFF",
				"lastcall": "0",
				"paused": "0",
				"manager": "n",
				"membername": "",
				"calls": "0",
				"announce_holdtime": "no",
				"wrapuptime": "0",
				"camp_id": "0",
				"lead_id": "0",
				"callid": "0",
				"channelid": "",
				"created_at": "2024-01-17 16:57:43",
				"updated_at": "2024-01-17 16:57:43",
				"deleted_at": null
			},

		],
		"agent": {
			"agentid": 828,
			"onHold": "0",
			"agent_code": "u251521119c5bf9249ca",
			"name": "JJSc tenant test agent",
			"autologoff": "15",
			"ackcall": "no",
			"wrapuptime": "0",
			"musiconhold": "agents",
			"updatecdr": "yes",
			"group": "",
			"recordagentcalls": "",
			"recordformat": "wav",
			"createlink": "yes",
			"urlprefix": "",
			"savecallsin": "",
			"custom_beep": "beep",
			"status": "LOGOFF",
			"statustime1": "2022-10-19 20:33:40",
			"tenantid": "138",
			"queue_name": "",
			"uniqueid": "0",
			"call_uniqueid": "",
			"loginstart": "0",
			"lastcall": "0",
			"paused": "0",
			"lasttime": null,
			"callid": "0",
			"loginunique": "",
			"holdchannel": "",
			"urllogin": "",
			"logintype": "GET",
			"urllogout": "",
			"logouttype": "GET",
			"urlbtwcalls": "",
			"btwcallstype": "GET",
			"gotoready": "n",
			"userid": "844",
			"_ROLES": "",
			"token": "",
			"callswaiting": "0",
			"clientversion": "",
			"latency": "0",
			"sqldelay": "0",
			"selectleaddelay": "0",
			"uuid": "",
			"agent_message": "",
			"deleted_at": null,
			"created_at": null,
			"updated_at": null,
			"Password": "s6P7v4K1"
		},
		"user_type": {
			"usertype": 27,
			"descripcion": "Agent",
			"newhomepage": "0",
			"homepage": "none",
			"can_create": "0",
			"scopes": "read",
			"showinadmin": "0",
			"created_at": "2018-08-03T05:05:47.000000Z",
			"updated_at": "2023-02-27T18:20:11.000000Z",
			"deleted_at": null,
			"roles": []
		}
	}
]
```

Agrega/modifica user


Crea todas las relaciones (agent.team, crea user en el cognito) y si ya existia un user con el mismo email le toma el passwd

`ADMIN => ` En screen user edit se ingresan todos los inputs y se procede a guardar, si userid == -1 es POST caso contrario es PUT

```php
$app->post('/user', \App\Controllers\UserController::class . ':modifyUser');
$app->put('/user', \App\Controllers\UserController::class . ':modifyUser');
```
```json
{
	"userid": "-1",
	"fullname": "test user 3",
	"email": "test_jjsc_user@callevo.com",
	"usertype": "27",
	"language": "en"
}
```

Borra el user por id (elimina sus relaciones agent y teams)

`ADMIN => ` En el screen de `users` se permite eliminar una vez que seleccione una fila.

```php
$app->delete('/user/{id}', \App\Controllers\UserController::class . ':deleteUser');
```

# ORDERS CONDITIONS 

`ADMIN => NO SE USA`

```php
$app->get('/orderconditions', \App\Controllers\OrderConditionController::class . ':listall')->setName('orderconditions');
$app->get('/ordercondition/{id}', \App\Controllers\OrderConditionController::class . ':getOrderCondition');
```
Recupera los conditions
```js
[
	{
		"ordertypeid": 1,
		"OrderName": "LeadID",
		"orderfields": "order by lead_id",
		"indexname": ""
	},
	{
		"ordertypeid": 2,
		"OrderName": "Attempts  and random",
		"orderfields": "order by reccalled, lead_id",
		"indexname": ""
	},
	{
		"ordertypeid": 3,
		"OrderName": "Random",
		"orderfields": "order by seed",
		"indexname": ""
	},
	
]
```


Adiciona/modifica

`ADMIN => YA NO SE USA`

```php
$app->post('/ordercondition', \App\Controllers\OrderConditionController::class . ':modifyOrderCondition');
$app->put('/ordercondition', \App\Controllers\OrderConditionController::class . ':modifyOrderCondition');
```
```js
{
  ordertypeid: $('#ordertypeid').val(), 
  OrderName:  $('#ordername').val(), 
  orderfields: $('#orderfields').val(), 
  indexname: $('#indexname').val() 
}
```

Borra

`ADMIN => YA NO SE USA`

```php
$app->delete('/ordercondition/{id}', \App\Controllers\OrderConditionController::class . ':deleteOrderCondition');
```

# UIPROJECT (external script)  

Recupera el project

`ADMIN => NO SE USA` Admin toma de sus modelos

```php
$app->get('/uiprojects', \App\Controllers\UIProjectController::class . ':getUiprojects');    
```
```json
{
	"status": "ok",
	"message": [
		{
			"projectid": 21,
			"projectname": "Midwest Project\/Script 1",
			"camp_id": "606",
			"tenantid": "172",
			"created": "2023-01-05T02:55:23.000000Z",
			"updated_at": "2023-01-05 02:55:23",
			"callpath": "",
			"u_i_script": [
				{
					"scriptid": 58,
					"title": "Script roust",
					"scriptName": "roust.twig",
					"description": "Script roust for campaign aws_test_cl",
					"created": "2023-01-05T02:55:23.000000Z",
					"lastmodified": "0000-00-00 00:00:00",
					"parameterlist": "T172C606\/roust.twig",
					"html_src": "PGRpdj5oZWxsbzwvZGl2Pg==",
					"logic_code": null,
					"alert_text": null
				}
			]
		},
		{
			"projectid": 22,
			"projectname": "Midwest Project\/Script 1",
			"camp_id": "606",
			"tenantid": "172",
			"created": "2023-01-16T13:08:34.000000Z",
			"updated_at": "2023-01-16 13:08:34",
			"callpath": "",
			"u_i_script": [
				{
					"scriptid": 66,
					"title": "Script roust",
					"scriptName": "roust.twig",
					"description": "Script roust for campaign aws_test_cl",
					"created": "2023-01-16T13:08:34.000000Z",
					"lastmodified": "0000-00-00 00:00:00",
					"parameterlist": "T172C606\/roust.twig",
					"html_src": "PGRpdj5oZWxsbzwvZGl2Pg==",
					"logic_code": null,
					"alert_text": null
				}
			]
		}
	]
}
```


`ADMIN => NO SE USA` Admin toma de sus modelos

```php
$app->get('/uiproject/{projectid}', \App\Controllers\UIProjectController::class . ':getUiproject');    
```
```json
{
	"status": "ok",
	"message": [
		{
			"projectid": 39,
			"projectname": "500001ak_0217_v4",
			"camp_id": "0",
			"tenantid": "200",
			"created": "-000001-11-30T00:00:00.000000Z",
			"updated_at": "0000-00-00 00:00:00",
			"callpath": "500001ak_0217_v4",
			"u_i_script": []
		}
	]
}
```

Adiciona/modifica

`ADMIN => ` Screen `External scripts`, opcion `edit` Guarda la informacion modificada

```php
$app->post('/uiproject', \App\Controllers\UIProjectController::class . ':modifyUiproject');    
$app->put('/uiproject/{projectid}', \App\Controllers\UIProjectController::class . ':modifyUiproject');    
```
Parametros de entrada
```js
{
    projectname: $("#projectname").val(),
    callpath: callpath.toLowerCase()
}
```
Parametros de salida
```json
{"status": 'ok', "message": 1032}
```
```json
{
    "projectname": "PDI test Project name",
	"camp_id": 347,
	"tenantid": 38,
	"u_i_script": [
		{
	       "title": "Script test",
		   "scriptName": "roust.twig",
		   "description": "Script for campaign pdi_test_cl test 2 ",
		   "html_src":"PGRpdiBjbGFzcz0iY29udGFpbm."
	    }
	]
} 
```

Borra
```php
$app->delete('/uiproject/{projectid}', \App\Controllers\UIProjectController::class . ':deleteUiproject'); 
```


Recupera todos los escripts del proyecto
```php
$app->get('/uiscript[/{projectid}]', \App\Controllers\UIProjectController::class . ':getUiscript');    
```
```
{
	"status": "ok",
	"message": [
		{
			"scriptid": 480,
			"title": "Script firewall old",
			"scriptName": "",
			"description": "Script firewall old",
			"projectid": "161",
			"parameterlist": "testsb\/firewall old",
			"tenantid": "138",
			"html_src": "IyBGaXJld2FsbCBj",
			"logic_code": "",
			"alert_text": "",
			"created": "2023-05-25T16:20:30.000000Z",
			"lastmodified": "0000-00-00 00:00:00",
			"startpage": "0"
		},
		{
			"scriptid": 482,
			"title": "Script List_Phones",
			"scriptName": "",
			"description": "Script List_Phones",
			"projectid": "161",
			"parameterlist": "testsb\/List_Phones",
			"tenantid": "138",
			"html_src": "bGVhZF9waG9uZSxsZ",
			"logic_code": "",
			"alert_text": "",
			"created": "2023-05-25T16:21:45.000000Z",
			"lastmodified": "0000-00-00 00:00:00",
			"startpage": "0"
		},
	
	]
}
```

Inserta/modifica un script para el proyecto

```
$app->post('/uiscript[/{projectid}]', \App\Controllers\UIProjectController::class . ':insertUiscript');   
$app->put('/uiscript/{scriptid}', \App\Controllers\UIProjectController::class . ':updateUiscript');    
```
Hace un parser del html separando las posibles preguntas, respuestas y botones (disp) para llenar las tablas correspondientes de external_script_questions y external_script_answers 
```
 {
	"scriptid":0,
	"title":"this the title",
	"description":"how to describe",
	"parameterlist":"500001ak_0215_v5/500001ak_0215_v5_Script",
	"html_src":"sdsfasdsd ",
	"alert_text":"dssdsf ",
	"logic_code":""
 }
```

Borra 
```
$app->delete('/uiscript/{scriptid}', \App\Controllers\UIProjectController::class . ':deleteUiscript');    
```

Establece el scriptid como pagina inicial de su proyecto
```
$app->post('/uiscript/startpage/{scriptid}', \App\Controllers\UIProjectController::class . ':startUiscript'); 
```
```
{
	"scriptid": 2323
}
```
Envia en un zip multiples scripts para un proyecto
$app->post('/upload_zipmultiscripts/{projectid}/{callpath}', \App\Controllers\UIProjectController::class .':uploadMultiScript'); 
Los files dentro del zip deben ser de la siguiente forma
page1.html,pasge2.twig   <- paginas html o en formato twig
page3.logic <- codigo html para ejecutar logicas 

Crea un reporte dinamico de la campaña a partir de los datos del script (questions,answers, dispositions)
$app->post('/report_from_external_script[/p/{p}/f/{f}/o/{o}/i/{i}]', \App\Controllers\UIProjectController::class . ':reportFromParseScript'); 
 {
    "camp_id": "1534",
    "rptdate_ini": "2024-09-03",
    "rptdate_end": "2024-09-04",
    "total_records": "0"
}


/**
 * =================   SURVEY (new scriptbuilder) ========================================
 */
 
Devuelve uno o mas survey 
$app->get('/surveys', \App\Controllers\SurveyController::class . ':getSurvey');
$app->get('/survey/{surveyid}', \App\Controllers\SurveyController::class . ':getSurvey');
{
	"status": "ok",
	"message": {
		"surveyid": 233,
		"survey_name": "hd31primary_script",
		"description": "hd31primary_script",
		"camp_id": "1230",
		"dispid": "0",
		"integration_type": "0",
		"tenantid": "201",
		"preface": "",
		"epilogue": "",
		"logo_url": "",
		"branch": "0",
		"sms": "0",
		"paththrough": "0",
		"callback": "0",
		"sendtext": "0",
		"status": "1",
		"created_at": "2024-02-13 16:40:40",
		"updated_at": null,
		"deleted_at": null,
		"logo": null,
		"logotype": "",
		"survey_actions_by_survey": [
			{
				"answerbysurveyid": 2801,
				"surveyid": "233",
				"questionid": "988",
				"answerid": "3121",
				"action": "NEXT",
				"nextquestion": null,
				"dispid": null,
				"flagid": null,
				"option": null,
				"quota_value": "0",
				"created_at": "2024-02-13 16:42:50",
				"updated_at": "2024-02-13 16:42:50",
				"deleted_at": null
			},

		],
		"survey_disposition_by_survey": [
			{
				"surveydispid": 10880,
				"surveyid": "233",
				"dispid": "6990",
				"active": "1",
				"caption": "Answering machine (agent detected)",
				"position": "0",
				"backcolor": "267bb5",
				"forecolor": "FFF",
				"order": "0",
				"created_at": "2024-02-13 16:42:50",
				"updated_at": "2024-02-13 16:42:50",
				"deleted_at": null,
				"disposition": {
					"dispid": 6990,
					"statusid": "6",
					"dispcode": "AMM",
					"dispdesc": "Answering machine (agent detected)",
					"success": "n",
					"contact": "n",
					"presentation": "n",
					"dnc": "n",
					"enabled": "y",
					"finalcrc": "n",
					"recall": "y",
					"recallscale": "0",
					"seconds": "14400",
					"rollover": "n",
					"rocamp_id": "0",
					"revenue": "0.00",
					"crcid": "0",
					"tenantid": "201",
					"created_at": "2023-02-17 19:00:47",
					"updated_at": "2023-02-17 19:00:47",
					"deleted_at": null,
					"vanresultid": "0",
					"integration_type": "0"
				}
			},
		
			}
		],
		"survey_question_by_survey": [
			{
				"surveyquestionid": 709,
				"surveyid": "233",
				"qtype": "0",
				"questionid": "988",
				"flagid": null,
				"segment": null,
				"position": "0",
				"autofill": "0",
				"required": "0",
				"created_at": "2024-02-13 16:42:50",
				"updated_at": "2024-02-13 16:42:50",
				"deleted_at": null,
				"data_type": "",
				"field_type": "",
				"field_target": "",
				"survey_questions": {
					"questionid": 988,
					"question": "<p><strong>Will you support Michael Crawford for state representative in the Democratic Primary Election?<\/strong><\/p>",
					"question_clean": "Will you support Michael Crawford for state representative in the Democratic Primary Election?",
					"description": "",
					"description_clean": "",
					"alternate": "",
					"alternate_clean": "",
					"question_type": "1",
					"integration_type": "0",
					"vanid": "0",
					"tenantid": "201",
					"userid": "0",
					"data_type": "",
					"field_type": "",
					"field_target": "",
					"data_entry_label": "",
					"data_entry_target": "",
					"logic_code": "",
					"alert": "",
					"created_at": "2024-02-13 16:42:50",
					"updated_at": "2024-02-13 16:42:50",
					"deleted_at": null,
					"datatype": "",
					"fieldtype": "",
					"target": "",
					"user": null,
					"survey_answers_by_questions": [
						{
							"answerquestionid": 4285,
							"questionid": "988",
							"answerid": "3121",
							"description": "YES",
							"position": "1",
							"created_at": "2024-02-13 16:42:50",
							"updated_at": "2024-02-13 16:42:50",
							"deleted_at": null,
							"survey_answers": {
								"answerid": 3121,
								"tenantid": "201",
								"answer": "Y",
								"description": "YES",
								"integration_type": "0",
								"vanid": "0",
								"created_at": "2024-02-13 16:42:50",
								"updated_at": "2024-02-13 16:42:50",
								"deleted_at": null,
								"disposition": null
							}
						},
			
					]
				},
				"survey_flags": null,
				"used": 0
			},
			
			
		],
		"campaign": {
			"camp_id": 1230,
			"camp_name": "hd31primary",
			"trunkID": "3",
			"camp_channels": "0",
			"ivrid": "0",
			"amdivrid": "0",
			"phoneID": "0",
			"tenantid": "201",
			"groupid": null,
			"camp_description": "",
			"active": "n",
			"started": "00:00:00",
			"camp_type": "CL",
			"ratio": "3:1",
			"status": "0",
			"inbound_number": "_cmp1230$$",
			"queue_name": "q201d117455304e0f7f7",
			"maxretrys": "5",
		.
		},
		"used": 0
	}
}


devuelve una lista abreviada
$app->get('/surveys_list', \App\Controllers\SurveyController::class . ':getSurveysList');
{
	"status": "ok",
	"message": [
		{
			"surveyid": "91",
			"survey_name": "testscriptone",
			"branch": "0",
			"paththrough": "0",
			"preface": "<p>Hello &nbsp;{{parser.CallLead.lead_fname}} , this is Afl Illinois calling to say HI<\/p>",
			"epilogue": "<p>Thank you for talking to me today. &nbsp;Have a great night<\/p>",
			"camp_name": "clickcampaignone",
			"question_count": "1",
			"used": "0"
		},
		{
			"surveyid": "135",
			"survey_name": "newtestscript",
			"branch": "0",
			"paththrough": "0",
			"preface": "<p>this is the preface &nbsp;{{parser.Agent.agent_fullname}}&nbsp;<\/p>",
			"epilogue": "<p>This is the epilogue {{parser.CallLead.lead_fullname}}&nbsp;<\/p>",
			"camp_name": "clickcampaignone",
			"question_count": "1",
			"used": "0"
		},
	]
}	

Inserta/modifica survey con o sin relaciones, si estas existen se actualizan o se crean
$app->post('/survey', \App\Controllers\SurveyController::class . ':modifySurvey');
$app->put('/survey[/{surveyid}]', \App\Controllers\SurveyController::class . ':modifySurvey');
{
    "survey_name": "Hoy will i Know",
    "description": "Hoy will i Know",
    "camp_id": "10",
    "tenantid": "86",
    "preface": "Este es un prefacio\ny se debe tratar como tal",
    "epilogue": "Este es un epilogo\ny tambien\nse debe tratar como tal",
    "branch": 1,
    "sms": 1,
    "paththrough": 1
	"survey_actions_by_survey" : [],
	"survey_question_by_survey": [],
	"survey_questions": []
}

Devuelve uno mas actions 
$app->get('/survey_actions', \App\Controllers\SurveyController::class . ':getSurveyActions');
$app->get('/survey_action/{actionid}', \App\Controllers\SurveyController::class . ':getSurveyActions');
{
	"status": "ok",
	"message": [
		{
			"actionid": 1,
			"name": "Next",
			"implicaction": "Next Question"
		},
		{
			"actionid": 2,
			"name": "Finish Survey",
			"implicaction": "Set dispo hang"
		},
	]
}	

Devuelve uno o mas registros con sus relaciones Survey, SurveyQuestions, SurveyAnswersByQuestions
$app->get('/survey_actions_by_survey', \App\Controllers\SurveyController::class . ':getActionBySurvey');
$app->get('/survey_action_by_survey/{answerbysurveyid}', \App\Controllers\SurveyController::class . ':getActionBySurvey');
{
	"status": "ok",
	"message": [
		{
			"answerbysurveyid": 67,
			"surveyid": "3",
			"questionid": "55",
			"answerid": "63",
			"action": "JUMP",
			"nextquestion": "56",
			"dispid": null,
			"flagid": null,
			"option": null,
			"quota_value": "0",
			"created_at": "2021-12-07 14:53:32",
			"updated_at": "2021-12-07 15:01:22",
			"deleted_at": null,
			"survey": null,
			"survey_questions": [
				{
					"questionid": 55,
					"question": "What is my name?",
					"question_clean": "",
					"description": "question 1",
					"description_clean": "",
					"alternate": "que es mi nombre",
					"alternate_clean": "",
					"question_type": "2",
					"integration_type": "0",
					"vanid": "0",
					"tenantid": "86",
					"userid": "442",
					"data_type": "",
					"field_type": "",
					"field_target": "",
					"data_entry_label": "",
					"data_entry_target": "",
					"logic_code": "",
					"alert": "",
					"created_at": "2021-11-19 17:56:05",
					"updated_at": "2021-12-30 15:59:48",
					"deleted_at": null,
					"datatype": "",
					"fieldtype": "",
					"target": "",
					"survey_answers_by_questions": [
						{
							"answerquestionid": 60,
							"questionid": "55",
							"answerid": "63",
							"description": "yes this an answer i need i will make this a really long answer so it is hard to save. 12312345235)()&*(&*(^*&%$^$%^$",
							"position": "0",
							"created_at": "2021-11-19 18:13:20",
							"updated_at": "2021-11-19 18:13:20",
							"deleted_at": null
						},
						{
							"answerquestionid": 64,
							"questionid": "55",
							"answerid": "2",
							"description": "Voting NO on recall (GOOD)",
							"position": "1",
							"created_at": "2021-11-30 16:55:27",
							"updated_at": "2021-11-30 16:55:27",
							"deleted_at": null
						}
					]
				}
			]
		},
	]
}	

Modifica/agrega un action sin relaciones
$app->post('/survey_action_by_survey', \App\Controllers\SurveyController::class . ':modifyActionBySurvey');
$app->put('/survey_action_by_survey/{answerbysurveyid}', \App\Controllers\SurveyController::class . ':modifyActionBySurvey');
{
	"answerbysurveyid": 67,
	"surveyid": "3",
	"questionid": "55",
	"answerid": "63",
	"action": "JUMP",
	"nextquestion": "56",
	"dispid": null,
	"flagid": null,
	"option": null,
	"quota_value": "0",
	"survey": null,
}	

Borra un action por id
$app->delete('/survey_action_by_survey/{answerbysurveyid}', \App\Controllers\SurveyController::class . ':deleteActionBySurvey');

Devuelve una o mas preguntas con sus relaciones (answers_by_questios,answers, action_by_survey, question_by _survey) 
$app->get('/survey_questions', \App\Controllers\SurveyController::class . ':getSurveyQuestions');
$app->get('/survey_question/{questionid}', \App\Controllers\SurveyController::class . ':getSurveyQuestions');
{
	"status": "ok",
	"message": {
		"questionid": 446,
		"question": "Make rick President",
		"description": "",
		"alternate": null,
		"question_type": "1",
		"integration_type": "1",
		"vanid": "481827",
		"tenantid": "97",
		"datatype": "inputbox",
		"fieldtype": "alphanumeric",
		"target": "",
		"userid": "0",
		"created_at": "2022-06-10 14:21:13",
		"updated_at": "2022-07-27 19:50:34",
		"deleted_at": null,
		"user": null,
		"survey_answers_by_questions": [
			{
				"answerquestionid": 1926,
				"questionid": "446",
				"answerid": "1825",
				"description": "VAN source",
				"position": "0",
				"created_at": "2022-06-10 14:21:13",
				"updated_at": "2022-07-27 20:03:08",
				"deleted_at": null,
				"survey_answers": {
					"answerid": 1825,
					"tenantid": "97",
					"answer": "YES",
					"description": "YES",
					"integration_type": "1",
					"vanid": "1964790",
					"created_at": "2022-06-10 14:21:13",
					"updated_at": null,
					"deleted_at": null,
					"disposition": null
				}
			},
			{
				"answerquestionid": 1927,
				"questionid": "446",
				"answerid": "1826",
				"description": "VAN source",
				"position": "0",
				"created_at": "2022-06-10 14:21:13",
				"updated_at": "2022-07-27 20:03:04",
				"deleted_at": null,
				"survey_answers": {
					"answerid": 1826,
					"tenantid": "97",
					"answer": "NO",
					"description": "NO",
					"integration_type": "1",
					"vanid": "1964791",
					"created_at": "2022-06-10 14:21:13",
					"updated_at": null,
					"deleted_at": null,
					"disposition": null
				}
			}
		],
		"survey_actions_by_survey": [
			{
				"answerbysurveyid": 569,
				"surveyid": "55",
				"questionid": "446",
				"answerid": "1825",
				"action": "NEXT",
				"nextquestion": null,
				"dispid": null,
				"flagid": null,
				"option": null,
				"quota_value": "0",
				"created_at": "2022-07-06 14:03:27",
				"updated_at": "2022-07-06 14:03:27",
				"deleted_at": null
			},
		],
		"survey_question_by_survey": [
			{
				"surveyquestionid": 261,
				"surveyid": "66",
				"qtype": "0",
				"questionid": "446",
				"flagid": null,
				"segment": "",
				"position": "0",
				"autofill": "0",
				"allowskip": "0",
				"created_at": "2022-07-27 19:51:43",
				"updated_at": "2022-07-27 19:51:49",
				"deleted_at": null
			},

		]
	}
}

Agrega/modifica question con o sin sus relaciones
$app->post('/survey_question', \App\Controllers\SurveyController::class . ':modifySurveyQuestions');
$app->put('/survey_question[/{questionid}]', \App\Controllers\SurveyController::class . ':modifySurveyQuestions');
{
		"questionid": 446,
		"question": "Make rick President",
		"description": "",
		"alternate": null,
		"question_type": "1",
		"integration_type": "1",
		"vanid": "481827",
		"tenantid": "97",
		"datatype": "inputbox",
		"fieldtype": "alphanumeric",
		"target": "",
		"userid": "0",
		"created_at": "2022-06-10 14:21:13",
		"updated_at": "2022-07-27 19:50:34",
		"deleted_at": null,
		"user": null,
		"survey_answers_by_questions": [
		],
		"survey_actions_by_survey": [
		],
		"survey_question_by_survey": [
		]
	}
}


Borra 
$app->delete('/survey_question/{questionid}[/{forcelib}]', \App\Controllers\SurveyController::class . ':deleteSurveyQuestions');
$app->delete('/survey_questions', \App\Controllers\SurveyController::class . ':deleteSurveyQuestions');

Devuelve uno o mas question by survey
$app->get('/survey_questions_by_survey', \App\Controllers\SurveyController::class . ':getQuestionBySurvey');
$app->get('/survey_question_by_survey/{surveyquestionid}', \App\Controllers\SurveyController::class . ':getQuestionBySurvey');
{
	"status": "ok",
	"message": [
		{
			"surveyquestionid": 8,
			"surveyid": "4",
			"qtype": "2",
			"questionid": null,
			"flagid": null,
			"segment": "This is free text  41.\tMembers shall not be required to sign a Non-Competition agreement, but they shall also observe the above-stated standards of personal integrity, and shall take no action that would be detrimental to the Company. 42.\tAny Member who fails to comply with all the provisions of this Agreement shall have his\/her Membership revoked by the other Members. 43.\tAny offer to buy the Company or its business shall be referred to the Members for evaluation.  The Members must agree unanimously in order to sell the Company or its business.     K.  Company Dissolution",
			"position": "0",
			"autofill": "0",
			"allowskip": "0",
			"created_at": "2021-11-30 15:33:55",
			"updated_at": "2021-11-30 15:33:55",
			"deleted_at": null,
			"survey": {
				"surveyid": 4,
				"survey_name": "ricktest1130",
				"description": "new description",
				"camp_id": "10",
				"dispid": "1009",
				"integration_type": "0",
				"tenantid": "86",
				"preface": "Suspendisse ullamcorper egestas felis ut convallis. In maximus rutrum risus, a egestas urna vehicula id. Etiam id ullamcorper magna, et mattis ante. Pellentesque orci lacus, aliquet quis lacus id, auctor pretium lacus. Suspendisse tempus tempor dui, ut euismod leo dictum a. Pellentesque tempor molestie elementum. Nulla facilisi. Sed ligula erat, convallis quis dapibus in, gravida a mi. \n\nDonec ultricies semper odio, at luctus dolor maximus vel. In hac habitasse platea dictumst. Integer leo enim, convallis vel luctus vitae, mattis laoreet leo. \n\nAliquam fringilla, risus ac convallis volutpat, dolor augue sodales felis, eu ullamcorper nunc augue semper lorem.\n\n4¿5'9'065¿'6045¿'6045¿'6045¿'603¿'02¿4'230¿'42342*3\/423-4*23423+423423\n4234234'092eopriwñfasd{f[ASDÑ[ASÑDAS[¨Q*WE¡!?#!¡?!#¡!¡#=$#%=#$%&?#$%&=34654645",
				"epilogue": "Proin eget iaculis velit. Aliquam gravida dui id risus pulvinar finibus. Sed ac hendrerit sem, vitae molestie elit. Etiam hendrerit eros venenatis libero tincidunt, vitae condimentum urna ultrices. Vestibulum sagittis interdum est. \n\nPellentesque in auctor dui. Interdum et malesuada fames ac ante ipsum primis in faucibus. Nulla tincidunt pharetra egestas. Cras gravida nisi tortor, id euismod nisi efficitur faucibus. Nulla cursus augue vitae dictum commodo.",
				"logo_url": "",
				"branch": "0",
				"sms": "0",
				"paththrough": "0",
				"callback": "0",
				"sendtext": "0",
				"status": "1",
				"created_at": "2021-11-30 15:32:45",
				"updated_at": "2021-11-30 16:42:50",
				"deleted_at": null,
				"logo": "",
				"logotype": ""
			},
			"survey_questions": null
		},
		.
	]
}	


Agrega/modifica question by survey (deben existir en la tabla questions)
$app->post('/survey_question_by_survey', \App\Controllers\SurveyController::class . ':modifyQuestionBySurvey');
$app->put('/survey_question_by_survey/{surveyquestionid}', \App\Controllers\SurveyController::class . ':modifyQuestionBySurvey');
{
    "surveyid": "1",
    "questionid": "11",
    "explanation": "Pregunta 11",
    "position": "-1"
}


Borra de la tabla question_by_survey (no toca questions)
$app->delete('/survey_question_by_survey[/{surveyquestionid}/{forcelib}]', \App\Controllers\SurveyController::class . ':deleteQuestionBySurvey');
{
	"surveyid": 1,
	"questionid": 11
}

Actualiza las posiciones de las preguntas
$app->put('/survey_question_by_survey_block/{surveyid}', \App\Controllers\SurveyController::class . ':modifyQuestionBySurveyInBlock');
 [
	 {"surveyquestionid":74,"position":0},
	 {"surveyquestionid":73,"position":1},
	 {"surveyquestionid":71,"position":2}
 ]
 
Chequea y arregla que las posiciones de las preguntas sean secuenciales sin saltos 
$app->post('/survey_question_positions/{surveyid}', \App\Controllers\SurveyController::class . ':checkSurveyQuestionPositions');	 


Devuelve el question_by_survey id con todas sus relaciones
$app->get('/survey_questions_by_surveyid/{surveyid}', \App\Controllers\SurveyController::class . ':getQuestionBySurveyID');
Ver el resultado arriba

Devuelve uno mo mas answer con sus relaciones
$app->get('/survey_answers', \App\Controllers\SurveyController::class . ':getSurveyAnswers');
$app->get('/survey_answer/{answerid}', \App\Controllers\SurveyController::class . ':getSurveyAnswers');
{
	"status": "ok",
	"message": [
		{
			"answerid": 2422,
			"tenantid": "25",
			"answer": "yes",
			"description": "YES",
			"integration_type": "0",
			"vanid": "0",
			"created_at": "2023-02-20 22:13:36",
			"updated_at": "2023-02-20 22:13:36",
			"deleted_at": null,
			"disposition": null,
			"survey_actions_by_survey": [
				{
					"answerbysurveyid": 1518,
					"surveyid": "92",
					"questionid": "669",
					"answerid": "2422",
					"action": "NEXT",
					"nextquestion": null,
					"dispid": null,
					"flagid": null,
					"option": null,
					"quota_value": "0",
					"created_at": "2023-04-24 15:24:01",
					"updated_at": "2023-04-24 15:24:01",
					"deleted_at": null
				},
			.
			],
			"survey_answers_by_questions": [
				{
					"questionid": "669",
					"position": "0",
					"used": 0
				},
				.
			]
		},

Agrega/modifica answers 
$app->post('/survey_answer', \App\Controllers\SurveyController::class . ':modifySurveyAnswers');
$app->put('/survey_answer/{answerid}', \App\Controllers\SurveyController::class . ':modifySurveyAnswers');
{
	"answerid": 2422,
	"tenantid": "25",
	"answer": "yes",
	"description": "YES",
	"integration_type": "0",
	"vanid": "0",
	"created_at": "2023-02-20 22:13:36",
	"updated_at": "2023-02-20 22:13:36",
	"deleted_at": null,
	"disposition": null,
},


Borra answers pot id (opcionalmente la elimina de la lib)
$app->delete('/survey_answer/{answerid}[/{forcelib}]', \App\Controllers\SurveyController::class . ':deleteSurveyAnswers');
Esta ruta se utiliza internamente para borrar mas du un ansewer si se envia los id separados por ,
$app->delete('/survey_answers', \App\Controllers\SurveyController::class . ':deleteSurveyAnswers');

Borra de la tabla answer by question
$app->delete('/survey_answer_by_question/{answerquestionid}[/{forcelib}]', \App\Controllers\SurveyController::class . ':deleteAnswerByQuestion');

Agrega/modifica un survey con asnswer y questions
$app->post('/survey_light[/{surveyid}]', \App\Controllers\SurveyController::class . ':modifySurveyLight');
$app->put('/survey_light/{surveyid}', \App\Controllers\SurveyController::class . ':modifySurveyLight');
 {
    "survey_name": "new test now_script",
    "description": "new test now_script",
    "camp_id": "1051",
    "integration_type": "0",
    "tenantid": "25",
    "preface": "",
    "epilogue": "",
    "branch": "0",
    "sms": "0",
    "paththrough": "0",
    "callback": "0",
    "sendtext": "0",
    "status": "1",
    "survey_questions": [
        {
            "surveyid": "-1",
            "questionid": "-1",
            "question": "<p>dasedasd<\/p>",
            "question_clean": "dasedasd",
            "question_type": "1",
            "integration_type": "0",
            "tenantid": "25",
            "data_type": "",
            "field_type": "",
            "field_target": "",
            "data_entry_label": "",
            "data_entry_target": "",
            "survey_answers": [
                {
                    "order": "1",
                    "answer": "aa",
                    "description": "aa",
                    "quota": "0"
                },
                {
                    "order": "2",
                    "answer": "ss",
                    "description": "ss",
                    "quota": "0"
                },
                {
                    "order": "3",
                    "answer": "aaaa",
                    "description": "aaaaa",
                    "quota": "0"
                }
							 ],
            "position": "0"
        }
    ]
}

Borra un survey id con sus relaciones (action, question y disposition) conserva los libs
$app->delete('/survey/{surveyid}', \App\Controllers\SurveyController::class . ':deleteSurvey');

Interna, borra los datos de un calltest
$app->delete('/surveycalltest/{callid}', \App\Controllers\SurveyController::class . ':deleteSurveyCallTest');


$app->get('/survey_contacts[/{surveyid}]', \App\Controllers\SurveyController::class . ':getContactButton');
[
	{
		"contact_id": 1,
		"label": "CallBack",
		"selected": false
	},
	{
		"contact_id": 2,
		"label": "Conference",
		"selected": false
	},
	{
		"contact_id": 3,
		"label": "Send Text",
		"selected": false
	}
]

Agrega buttos contacts
$app->post('/survey_contact[/{surveyid}]', \App\Controllers\SurveyController::class . ':modifyContactButton');
{
	"contact_id": 3,
	"label": "Send Text",
	"selected": false
}


Agrega disposition por surveyid
$app->post('/survey_disposition_by_survey/{surveyid}', \App\Controllers\SurveyController::class . ':modifyDispositionBySurvey');
[
	"surveyid" => $surveyid,
	"dispid" => $value["dispid"],
	"active" => $value["active"],
	"caption" => $value["caption"],
	"position" => $value["position"] ?? 0,
	"backcolor" => $value["backcolor"],
	"forecolor" => $value["forecolor"],
	"order" => $value["order"],
	"quelog_action" => $value["quelog_action"] ?? "SETDISPHANG",
	
];

Variante de la anterior pero si existe se actualiza
$app->post('/disposition_by_survey/{surveyid}', \App\Controllers\SurveyController::class . ':modifyDispositionBySurvey2');

Duplica un surveyid
$app->post('/survey_clone/{surveyid}', \App\Controllers\SurveyController::class . ':cloneSurvey');

Devuelve todas las camp que tienen el surveyid
$app->get('/survey_campaigns/{surveyid}', \App\Controllers\SurveyController::class . ':getSurveyCampaigns');
{
	"status": "ok",
	"message": [
		{
			"camp_id": 10,
			"camp_name": "testone2",
			"urlcall": 1
		},
		{
			"camp_id": 11,
			"camp_name": "testmanual",
			"urlcall": 1
		},
		
	]
}	

Actualiza el urlcall de todas las camp del tenant con el surveyid
$app->post('/survey_campaigns/{surveyid}', \App\Controllers\SurveyController::class . ':postSurveyCampaigns');

Determina si la pregunta esta usada
$app->get('/survey_get_used_question', \App\Controllers\SurveyController::class . ':getUsedQuestion');
{
	"camp_id" : 456
	"tenantid" : 138
	"questionid" : 234
	"surveyid" : 23 
	"var" : "q1"
}		


Devuelve uno o mas leadflags
$app->get('/leadsflag', \App\Controllers\SurveyController::class . ':getLeadFlag');
$app->get('/leadflag/{flagid}', \App\Controllers\SurveyController::class . ':getLeadFlag');
{
	"status": "ok",
	"message": [
		{
			"flagid": 1,
			"type": "Activist",
			"name": "Q51",
			"flagcode": "Q51",
			"description": "Q51",
			"surveyquestion": "Q51",
			"multiassign": "0",
			"tenantid": "86",
			"integration_type": "1",
			"vanid": "4973626"
		},
		
	]
}


Agrega/actuliza leadflags
$app->post('/leadflag', \App\Controllers\SurveyController::class . ':modifyLeadFlag');
$app->put('/leadflag/{flagid}', \App\Controllers\SurveyController::class . ':modifyLeadFlag');
{
	"flagid": 1,
	"type": "Activist",
	"name": "Q51",
	"flagcode": "Q51",
	"description": "Q51",
	"surveyquestion": "Q51",
	"multiassign": "0",
	"tenantid": "86",
	"integration_type": "1",
	"vanid"
}

Borra leadflag por su id
$app->delete('/leadflag/{flagid}', \App\Controllers\SurveyController::class . ':deleteLeadFlag');
Variante interna para borrar muchos id si estos estan separados por ,
$app->delete('/leadflags', \App\Controllers\SurveyController::class . ':deleteLeadFlag');

Crea un reporte dinamico segun estructura de preguntas, respuestas y disposition 
$app->post('/report_from_survey[/p/{p}/f/{f}/o/{o}/i/{i}]', \App\Controllers\SurveyController::class . ':reportFromSurvey');


/**
* ====================== INVITATION ==========================
*/

Genera un key para invitation
$app->post('/invitation_generate', \App\Controllers\UserController::class . ':invitationGenerate');
entrada:
 {
    "page": "users",
    "usertype": "27",
    "campid": "1646",
	 "tenantid": 258
}
Salida
{
	"status": "ok",
	"message": "https:\/\/invitation.callevo.net?key=LGqDwkXqLVKrTg58q5FjRo5tRejlmvS5kJfi3xNnIzVUrBg3aO4YQvXfE1VlsW7OdWVWdRsUc1zsoZkGMEW8q4APKxTyxF_ft585Ig"
}

VAlida la invitacion
$app->post('/invitation_validate', \App\Controllers\UserController::class . ':invitationValidate');
entrada
{
	"key" : "2_BUlrlb09GuR50e0mHJGPxng_Hfh4CADCFIhCoF8vu_fbQjsJeLkO5dnOmhyCRTCb5VAEoMjBdjt3cMkz-j7NvARRBzBxYvmU2uIp0"
}
salida
{
	"status": "ok",
	"message": {
		"page": "users",
		"camp_id": 890,
		"usertype": 27,
		"tenantid": "138"
	}
}

Realiza la creacion del user invitado, si el user ya tenia el email registrado toma el passwd y se lo asigna al nuevo que esta creando
$app->post('/signup_user', \App\Controllers\UserController::class . ':signUp');
entrada
{
    "email":"santiago.borja1@gmail.com",
	"pass":"NdhG8dFvWED",
	"fullname":"Santiago_Pruebas",
	"phone_number":"_593995918919",
	"locale":"en",
	"key":"v_kzRwPZtrRg4BO8VCZeQclmItx2A3WRkpRTF920aFya6oF4Df3XauRozyA6MtMtPLqM-dTt-QGJuBdflwcHT-BPtqFIpJvhiMntNg"
}
salida
{
	"status": "Ok",
	"message": {
		"email": "santiago.borja1@gmail.com",
		"password": "NdhG8dFvWED",
		"usertype": 30
	}
}

/**
* ============================== FAQ routes ====================================
*/

Lista una o mas 
$app->get('/faqs[/p/{p}/f/{f}/o/{o}/i/{i}]', \App\Controllers\FAQController::class . ':listFAQ');
$app->post('/faqs[/p/{p}/f/{f}/o/{o}/i/{i}]', \App\Controllers\FAQController::class . ':listFAQ');
entrada
{
	"total_records":"0",
	"fields":"faq_id,title,content,keywords,status",
	"where":" (title like '%projects%' OR content like '%projects%' OR keywords like '%projects%') ",
	"order":"faq_id"
}
salida
{
	"status": "ok",
	"message": [
		{
			"faq_id": "17",
			"title": "How to change calling speed",
			"content": "<p><strong>Speeding up or slowing down your calling<\/strong<\/p>",
			"keywords": "CALLING",
			"status": "1"
		},
		{
			"faq_id": "19",
			"title": "How to start and stop campaigns",
			"content": "<p><img alt=\"campaigns-started.jpg\" src=\"https:\/\/assets.callevo.net\/faqs\/campaigns-started.jpg\" style=\"float:right; height:154px; margin:10px; width:75px\" \/>You can see which campaigns are currently started on both the <strong>Campaigns | Activity<\/strong>&nbsp;and <strong>Administration | Project<\/strong>&nbsp;pages - look at the <strong>Status (S)<\/strong>&nbsp;column.&nbsp; Go to&nbsp;<strong>Administration | Projects<\/strong>&nbsp;(click&nbsp;<a href=\"\/projects\">here<\/a>).&nbsp; Select the project (campaign) that you want to start or stop.&nbsp; Click on the Start \/ Stop button above the list of projects.<\/p>",
			"keywords": "calling campaigns getting_started",
			"status": "1"
		},
		.
	]
}
$app->get('/faq[/{id}]', \App\Controllers\FAQController::class . ':listFAQ');
{
	"faq_id": "17",
	"title": "How to change calling speed",
	"content": "<p><strong>Speeding up or slowing down your calling<\/strong<\/p>",
	"keywords": "CALLING",
	"status": "1"
},

Agrega/modifica
$app->post('/faq', \App\Controllers\FAQController::class . ':modifyFAQ');
$app->put('/faq/{id}', \App\Controllers\FAQController::class . ':modifyFAQ');
{
	"faq_id": "17",
	"title": "How to change calling speed",
	"content": "<p><strong>Speeding up or slowing down your calling<\/strong<\/p>",
	"keywords": "CALLING",
	"status": "1"
},

Borra por ID
$app->delete('/faq/{id}', \App\Controllers\FAQController::class . ':deleteFAQ');


/**
* ============================= DID Rotation (group phones) ==========================================
*/
Lista uno o mas con sus relaciones
$app->get('/caller_id_groups', \App\Controllers\PhoneController::class . ':getCallerIdGroup');
$app->get('/caller_id_group/{groupid}', \App\Controllers\PhoneController::class . ':getCallerIdGroup');
{
	"status": "ok",
	"message": [
		{
			"groupid": 77,
			"camp_id": "0",
			"tenantid": "25",
			"group_name": "TEST",
			"created_at": "2023-08-22 21:02:14",
			"updated_at": "2023-08-22 21:02:14",
			"phone": [
				{
					"phoneid": 2664,
					"groupid": "77",
					"phone": "7203014913",
					"ptypeid": "1",
					"description": "test",
					"taken": "n",
					"tenantid": "25",
					"active": "1",
					"calls": "143",
					"totalcalls": "143",
					"prefixid": "196",
					"stateid": "7",
					"ratecenter": "",
					"flagged": "1",
					"flag_result": "",
					"created_at": "2022-09-26 21:07:29",
					"updated_at": "2023-10-18 16:09:53",
					"deleted_at": null,
					"phoneid_fk": "1325"
				},
				.
			],
			"dials": 285,
			"atc": 142.5
		},
		.
	]
}

Agrega/modifica
$app->post('/caller_id_group', \App\Controllers\PhoneController::class . ':modifyCallerIdGroup');
$app->put('/caller_id_group/{groupid}', \App\Controllers\PhoneController::class . ':modifyCallerIdGroup');
entrada
 {
    "groupid": "",
    "group_name": "otro_mas",
    "phone": [
        {
            "phoneid": "4501"
        },
        {
            "phoneid": "4539"
        },
        {
            "phoneid": "4519"
        }
    ],
    "camp_id": "1330"
}
salida
{
	"status": "ok",
	"message": {
		"groupid": 234,
		"message": [
			"inserted"
		]
	}
}

Borra por ID
$app->delete('/caller_id_group/{groupid}', \App\Controllers\PhoneController::class . ':deleteCallerIdGroup');

Lista los phoes del grupo
$app->get('/phones_caller_id/{groupid}', \App\Controllers\PhoneController::class . ':getPhoneInCallerId');
{
	"status": "ok",
	"message": [
		{
			"phonesincallergroup_id": "1",
			"groupid": "1",
			"phoneid": "49",
			"phone": null
		},
		{
			"phonesincallergroup_id": "2",
			"groupid": "1",
			"phoneid": "50",
			"phone": null
		}
	]
}
Devuelve uno por id
$app->get('/phone_caller_id/{phonesincallergroup_id}', \App\Controllers\PhoneController::class . ':getPhoneInCallerId');
{
	"phonesincallergroup_id": "2",
	"groupid": "1",
	"phoneid": "50",
	"phone": null
}

Borra por ID
$app->delete('/phones_caller_id[/{groupid}]', \App\Controllers\PhoneController::class . ':deletePhoneInCallerId');

Lista los estados
$app->get('/usa_states', \App\Controllers\StateController::class . ':usaStates');
{
	"status": "ok",
	"message": {
		"AK": "Alaska",
		"AL": "Alabama",
		"AR": "Arkansas",
		"AS": "American Samoa",
		"AZ": "Arizona",
		"CA": "California",
		"CO": "Colorado",
		"CT": "Connecticut",
		"DC": "District of Columbia",
		"DE": "Delaware",
		"FL": "Florida",
		"FM": "Federated States of Micronesia",
		"GA": "Georgia",
		"GU": "Guam",
		
	]
}	

Lista por estado
$app->get('/rate_centers/{state}', \App\Controllers\PhoneController::class . ':getRateCenters');
{
	"status": "ok",
	"message": [
		{
			"state": "AL",
			"ratecenter": "ABBEVILLE",
			"areacodes": [
				"334"
			]
		},
		
	]
}

/*
* ================= CALL RESULT MODIFICATION=====================
*/
Reportes
$app->put('/calllist/{id}', \App\Controllers\CallListController::class . ':callListSave');
$app->post('/call_history', \App\Controllers\CallListController::class . ':callHistory');

Recoge los dispo por campaña
$app->get('/disposition_by_campaign/{camp_id}', \App\Controllers\DispositionController::class . ':getDispositionByCampaign');
[
	{
		"dcid": 14995,
		"dispid": "2399",
		"camp_id": "433",
		"clientcode": "",
		"qcenabled": "n",
		"disposition": {
			"dispid": 2399,
			"statusid": "1",
			"dispcode": "MANUAL",
			"dispdesc": "Manual call",
			"success": "n",
			"contact": "n",
			"presentation": "n",
			"dnc": "n",
			"enabled": "y",
			"finalcrc": "n",
			"recall": "n",
			"recallscale": "0",
			"seconds": "0",
			"rollover": "n",
			"rocamp_id": "0",
			"revenue": "0.00",
			"crcid": "0",
			"tenantid": "139",
			"created_at": "2022-11-18 20:34:36",
			"updated_at": "2022-11-18 20:34:36",
			"deleted_at": null,
			"vanresultid": "0",
			"integration_type": "0"
		}
	},
	
]

Por tenant
$app->get('/disposition_by_tenant/{id}', \App\Controllers\DispositionController::class . ':getDispositionByTenant');
[
	{
		"dispid": 623,
		"statusid": "1",
		"dispcode": "LEAD",
		"dispdesc": "NEW LEAD",
		"success": "y",
		"contact": "y",
		"presentation": "y",
		"dnc": "y",
		"enabled": "n",
		"finalcrc": "y",
		"recall": "n",
		"recallscale": "0",
		"seconds": "0",
		"rollover": "n",
		"rocamp_id": "32",
		"revenue": "0.00",
		"crcid": "0",
		"tenantid": "139",
		"created_at": "2022-11-19 00:03:30",
		"updated_at": "2022-11-19 00:03:30",
		"deleted_at": null,
		"vanresultid": "0",
		"integration_type": "0",
		"status": {
			"statusid": 1,
			"statusname": "Person",
			"resetable": "1",
			"exportable": "0",
			"order": "1"
		}
	},
	.
]	

Retorna el unique id del call id
$app->get('/call/{id}', \App\Controllers\CallsController::class . ':getCallUniqueID');

Realiza una busqueda (query) en opensearch usando curl 
$app->get('/opensearchquery', \App\Controllers\CurlController::class . ':openSearchQuery');


/*
* ========================= MANAGEMENT (POOLS) ==================================
*/
Archiva/restaura un pool usando s3
$app->post('/archive_pool/{poolid}', \App\Controllers\PoolController::class . ':archivePool');
$app->get('/archive_pool/{poolid}', \App\Controllers\PoolController::class . ':archivePool');

Funcion antigua para hacer los pasos de importacion
$app->post('/importer/{id}/{op}', \App\Controllers\PoolController::class . ':importer');

Funcion actual que hace los pasos de importacion a un pool previamente subido al s3
$app->post('/file_import/{id}', \App\Controllers\PoolController::class . ':fileImport');
error,dedup,scrub,merge

Usa las tablas pools y campaign_pool para verificar si el pool esta importado correctamente
$app->get('/check_real_import/{id}', \App\Controllers\PoolController::class . ':checkRealImport');
resultado
{ 
	"status": "ok",
	"id" : 2234
}

Templates management
Devuelve un template por su id o por line

`ADMIN =>` Archivo `Importer` filesready permite obtener un template

```php
$app->get('/file_template', \App\Controllers\TemplateController::class . ':getFileTemplatebyLine');
$app->get('/file_template/{id}', \App\Controllers\TemplateController::class . ':getFileTemplate');
```
```json
{
	"id": 936,
	"tenantid": "201",
	"template_name": "elist121423.csv-template",
	"file_header": "Last,First,Card,Home Phone,Other Phone,Personal Email,Other Email,Work Group,Shift,Job Classification,Notes,Home Address,City,State,Zip,primaryid",
	"listline": "lead_lname,lead_fname,custom1,lead_phone,lead_email,custom2,custom3,custom4,lead_notes,lead_address,lead_city,lead_state,lead_zip,primaryid",
	"listnumbers": "3,1,23,4,-1,5,-1,24,25,26,19,6,12,13,14,73",
	"created_at": "2023-12-19T02:57:38.000000Z",
	"updated_at": "2023-12-19T02:59:08.000000Z",
	"deleted_at": null,
	"fields": [
		{
			"id": 13375,
			"field_name": "Last",
			"field_source": "Last",
			"field_destination": "lead_lname",
			"file_template": "936",
			"created_at": "2023-12-19T02:57:38.000000Z",
			"updated_at": "2023-12-19T02:59:08.000000Z",
			"deleted_at": null
		},
		{
			"id": 13376,
			"field_name": "First",
			"field_source": "First",
			"field_destination": "lead_fname",
			"file_template": "936",
			"created_at": "2023-12-19T02:57:38.000000Z",
			"updated_at": "2023-12-19T02:59:08.000000Z",
			"deleted_at": null
		},
		.
	}
}	
```


$app->get('/template_by_option', \App\Controllers\TemplateController::class . ':getFileTemplatebyLine');
Igual a la anterior pero usando el file_header, ejemplo:
https://apidev.callevo.net/api/public/template_by_option?file_header=Y3VzdG9tMSxJbnZvaW 
El header debe ser codificado en base64

Crea/modifica un template
$app->post('/save_template[/{poolid}]', \App\Controllers\TemplateController::class . ':templateSave')->setName('template_save');
$app->put('/save_template[/{poolid}]', \App\Controllers\TemplateController::class . ':templateSave');
$app->put('/template[/{poolid}]', \App\Controllers\TemplateController::class . ':templateSave');
{
	"file_template": {
		"id": -1,
		"template_name": "JJSC_PDI_test_file.csv-template"
	},
	"file_template_fields": [
		{
			"field_name": "Lead Fname",
			"field_source": "lead_fname",
			"field_destination": "lead_fname"
		},
		{
			"field_name": "Lead Lname",
			"field_source": "lead_lname",
			"field_destination": "lead_lname"
		},
		
	}
}

Borra un template simpre que no este en uso
$app->delete('/template/{id}', \App\Controllers\TemplateController::class . ':templateDelete');

Devuelve todos los templates con sus relaciones
$app->get('/file_templates', \App\Controllers\TemplateController::class . ':indexTemplate')->setName('templates');
[
	{
		"id": 28,
		"tenantid": "86",
		"template_name": "minagent_file.csv-template",
		"file_header": "lead_fname,lead_lname,lead_phone,custom1,conferencenumber,inlinecallid,recordingidname,smsnumber",
		"listline": "lead_fname,lead_lname,lead_phone,custom1,conferencenumber,inlinecallid,recordingidname,smsnumber",
		"listnumbers": "1,3,4,23,78,56,72,158",
		"created_at": "2021-09-17T13:51:11.000000Z",
		"updated_at": "2021-09-17T20:51:24.000000Z",
		"deleted_at": null,
		"fields": [
			{
				"id": 185,
				"field_name": "Lead Fname",
				"field_source": "lead_fname",
				"field_destination": "lead_fname",
				"file_template": "28",
				"created_at": "2021-09-17T13:51:11.000000Z",
				"updated_at": "2021-09-17T20:51:24.000000Z",
				"deleted_at": null
			},
			.
		]
	}
]
			
Determina si el template esta bloqueado porque ya esta en uso en un pool importado
$app->get('/is_template_lock/{id}', \App\Controllers\TemplateController::class . ':isTemplateLock')->setName('template_lock');
resultado
no|yes

Duplica el template 
$app->get('/duplicate_template/{id}[/{poolid}]', \App\Controllers\TemplateController::class . ':duplicateTemplate')->setName('duplicate_template');

Funciones internas para el admin
Devuelve el template id asignado al poolid
$app->get('/pool/template_edit[/{id}[/{poolid}[/{campid}]]]', \App\Controllers\TemplateController::class . ':templateEdit')->setName('template_edit');
{
	"status": "ok",
	"message": {
		"templateFields": [
			{
				"id": 6914,
				"field_name": "Lead Fname",
				"field_source": "lead_fname",
				"field_destination": "lead_fname",
				"file_template": "503",
				"created_at": "2022-10-20T14:31:41.000000Z",
				"updated_at": "2022-10-20T14:31:57.000000Z",
				"deleted_at": null
			},
			{
				"id": 6915,
				"field_name": "Lead Lname",
				"field_source": "lead_lname",
				"field_destination": "lead_lname",
				"file_template": "503",
				"created_at": "2022-10-20T14:31:41.000000Z",
				"updated_at": "2022-10-20T14:31:57.000000Z",
				"deleted_at": null
			},
			
		],
		"destColumns": [
			{
				"idx": 0,
				"value": "age"
			},
			{
				"idx": 2,
				"value": "allow_inbound"
			},
			{
				"idx": 4,
				"value": "callnotes"
			},
			{
				"idx": 6,
				"value": "canvassfilerequestid"
			},
			{
				"idx": 8,
				"value": "city"
			},
			
		],
		"destJColumns": "W3siaWR4IjowLCJ2YWx1ZSI6ImFnZSJ9LHsiaWR",
		"opt": "",
		"file_template": "503",
		"template_name": "JJSC_test_file3.csv-template",
		"poolid": "1664",
		"poolfile": "JJSC_test_file3.csv",
		"id": "503"
	}
}
Adiciona/modifica un template
$app->post('/pool/template_save[/{poolid}]', \App\Controllers\TemplateController::class . ':templateSave')->setName('template_save');
$app->put('/pool/template_save[/{poolid}]', \App\Controllers\TemplateController::class . ':templateSave');
Borra un template mientras no este usado
$app->delete('/pool/template_delete[/{id}]', \App\Controllers\TemplateController::class . ':templateDelete')->setName('template_delete');

Adiciona/modifica un pool
$app->post('/save_pool', \App\Controllers\PoolController::class . ':savePool');
$app->put('/save_pool', \App\Controllers\PoolController::class . ':savePool');
{
  "data": {
		"poolid":-1,
		"camp_id":612,
		"poolname":"new_file_test3.csv",
		"allow_duplicate":"n",
		"templateid":"534",
		"tenantid":"172",		
		"filecontent":"Zmlyc3RfbmFtZSxsYXN0X25hbWUscGhvbmVfbnVtY"
   }
}
Pone datos de importacion a 0 en pools y campaign_pool 
$app->post('/rollback_pool_imported/{poolid}', \App\Controllers\PoolController::class . ':rollbackPoolImported');

Eliminan los datos del pool y del template de la db
$app->delete('/cancel_pool/{id}', \App\Controllers\PoolController::class . ':cancelPool');
$app->delete('/cancel_template/{id}', \App\Controllers\PoolController::class . ':cancelTemplate');

Realiza varias verificaciones en el pool
$app->get('/check_pool/{id}', \App\Controllers\PoolController::class . ':checkPool');
- Template sin lead_phone
- Datos no importados
- Asignacion de camp incorrecta

Adiciona/modifica pool, al ser usado por admin, este ya determino los campos legacy listline,listnumber y firstline
$app->post('/pool/add', \App\Controllers\PoolController::class . ':savePool');
$app->put('/pool/add', \App\Controllers\PoolController::class . ':savePool');
{
	"data": {
		 "camp_id":2,
		 "poolname":"RickTestnumbers-test2.csv",
		 "allow_duplicate":"f",
		 "randomize":"y",
		 "CleanOld":"0",
		 "prefixlen":"3",
		 "templateid":26,
		 "imported":0,
		 "tenantid":25,
		 "listline":"bGVhZF9mbmFtZSxsZWFkX2xuYW1lLGxlYWRfcGhvbmUsY3VzdG9tMSxpbmxpbmVjYWxsaWQscmVjb3JkaW5naWRuYW1l",
		 "listnumbers":"MSwzLDQsMTgsLTEsNDQsNDc=",
		 "firstline":"bGVhZF9mbmFtZSxsZWFkX2xuYW1lLGxlYWRfcGhvbmUsY3VzdG9tMSxpbmxpbmVjYWxsaWQscmVjb3JkaW5naWRuYW1l",
		 "totalrecords":20,
		 "poolfile":"C: \\\\fakepath\\\\RickTestnumbers-test2.csv",
		 "filecontent":"bGVhZF9mbmFtZSx",
		"poolid":-1
		}
}

Borra el pool por id
$app->delete('/pool/delete/{id}', \App\Controllers\PoolController::class . ':deletePool');
$app->delete('/pool/{id}', \App\Controllers\PoolController::class . ':deletePool');

Estas funciones estan usadas via NATS, en api invocan a los SP correspondientes StartPool y StopPool
$app->get('/stop_pool/{id}', \App\Controllers\PoolController::class . ':stoppool');
$app->get('/start_pool/{id}', \App\Controllers\PoolController::class . ':startpool');
$app->get('/pool/stop/{id}', \App\Controllers\PoolController::class . ':stoppool');
$app->get('/pool/start/{id}', \App\Controllers\PoolController::class . ':startpool');

Devuelve la cantidad de records en dialer_leads que corresponde al pool
$app->get('/pool/count/{id}', \App\Controllers\PoolController::class . ':countRecordsPool');
salida
13456

// DEDUPER action
Nunca se han usado no tengo como hacer ejemplos, en deduper se arman queries dinamicos en base a condiciones 
$app->get('/target_counts', \App\Controllers\DeDuperController::class . ':targetCounts')->setName('targetcount');
$app->get('/deduper', \App\Controllers\DeDuperController::class . ':deDuper')->setName('deduper');
$app->put('/deduper', \App\Controllers\DeDuperController::class . ':deDuper');

Exporta en formato csv los datos de dialer_leads que corresponden al pool
$app->get('/leads/export/{poolid}', \App\Controllers\LeadController::class . ':leadExport');
$app->post('/leads/export/{poolid}', \App\Controllers\LeadController::class . ':leadExport');

Actualiza dialer_leads y calls
$app->post('/leads/qualitycheck/{leadid}', \App\Controllers\LeadController::class . ':leadQualityCheck');
{
	"leads": {
        "agentid": $("#agentid option:selected").val(),
        "lastcallresult": $("#lastcallresult option:selected").val(),
        "qad": $("#qad").val(),
        "qcresult": $("#qcresult option:selected").val(),
        "lead_fname": $("#lead_fname").val(),
        "lead_mname": $("#lead_mname").val(),
        "lead_lname": $("#lead_lname").val(),
        "lead_phone": $("#lead_phone").val(),
        "prefix": $("#prefix").val(),
        "seed": $("#seed").val(),
        "priority": $("#priority").val(),
        "fcalldata": $("#fcalldata").val(),
        "lead_city": $("#lead_city").val(),
        "lead_state": $("#lead_state").val(),
        "lead_zip": $("#lead_zip").val(),
        "lead_email": $("#lead_email").val(),
        "lead_description": $("#lead_description").val(),
        "lead_website": $("#lead_website").val(),
        "lead_title": $("#lead_title").val(),
        "private": $("#private").val(),
        "lead_company": $("#lead_company").val(),
        "lead_apto": $("#lead_apto").val(),
        "callnotes": $("#callnotes").val(),
        "lead_notes": $("#lead_notes").val(),
        "custom": $("#custom").val(),
        "custom1": $("#custom1").val(),
        "custom2": $("#custom2").val(),
        "custom3": $("#custom3").val(),
        "custom4": $("#custom4").val(),
        "custom5": $("#custom5").val(),
        "custom6": $("#custom6").val(),
        "custom7": $("#custom7").val(),
        "custom8": $("#custom8").val(),
        "custom9": $("#custom9").val(),
        "custom10": $("#custom10").val(),
        "custom11": $("#custom11").val(),
        "custom12": $("#custom12").val(),
        "custom13": $("#custom13").val(),
        "custom14": $("#custom14").val(),
        "custom15": $("#custom15").val(),
        "custom16": $("#custom16").val(),
        "custom17": $("#custom17").val(),
        "custom18": $("#custom18").val(),
        "custom19": $("#custom19").val(),
        "custom20": $("#custom20").val(),
        "lead_phone1": $("#phone1").val(),
        "lead_phone2": $("#phone2").val(),
        "lead_phone3": $("#phone3").val(),
        "lead_phone4": $("#phone4").val(),
        "lead_phone5": $("#phone5").val(),
        "lead_status": $("#lead_status").val(),
        "primaryid": $("#primaryid").val(),
        "party": $("#party").val(),
        "gender": $("#gender").val(),
        "age": $("#age").val(),
        "lead_fullname": $("#lead_fullname").val(),
        "permav": $("#permav").val(),
        "support": $("#support").val(),
        "congdist": $("#congdist").val(),
        "statesenatedist": $("#statesenatedist").val(),
        "statehousedist": $("#statehousedist").val(),
        "polldesc1": $("#polldesc1").val(),
        "polldesc2": $("#polldesc2").val(),
        "polladdress1": $("#polladdress1").val(),
        "exported": $("#exported").val(),
        "revenue": $("#revenue").val(),
        "lastreset": $("#lastreset").val(),
        "smsnumber": $("#smsnumber").val(),
        "uuidfield": $("#uuidfield").val(),
        "myuniqueid": $("#myuniqueid").val(),
    },
	"callsdata": {
		"callid": id,
		"agentid": agent,
		"agentdisp": dispo
	},
};

/*
* ========================= STATISTIC/DIALTABLE ==================================
*/
Lista uno mas pool stats con sus relaciones
$app->get('/poolstats[/{id}]', \App\Controllers\PoolController::class . ':listPoolStats')->setName('poolStats');
$app->get('/poolstat/{id}', \App\Controllers\PoolController::class . ':getPoolStat');
[
	{
		"poolid": 969,
		"pooluploadname": "",
		"poolname": "IX306B-3019Reverseskip-USEABLE.csv",
		"poolfile": "IX306B-3019Reverseskip-USEABLE.csv",
		"pooldate": "2023-05-11 13:44:24",
		"firstline": "custom,lead_fname,lead_lname,lead_address,lead_city,lead_state,lead_zip,lead_phone,lead_phone1,lead_phone2,lead_phone3,lead_phone4,lead_email",
		"totalrecords": "15318",
		"dedupopts": "n",
		"errors": "0",
		"dbPool": "0",
		"odbc": "",
		"config": "",
		"prefixlen": "3",
		"randomize": "y",
		"listnumbers": "22,1,3,6,12,13,14,4,50,51,52,53,5",
		"listline": "custom,lead_fname,lead_lname,lead_address,lead_city,lead_state,lead_zip,lead_phone,lead_phone1,lead_phone2,lead_phone3,lead_phone4,lead_email",
		"sqlstring": null,
		"camp_id": "433",
		"FieldCond": "",
		"OperCond": "",
		"ValueCond": "",
		"CleanOld": "0",
		"tenantid": "139",
		"templateid": "520",
		"imported": "1",
		"startstop": "0",
		"created_at": "2023-05-11T13:44:24.000000Z",
		"updated_at": "2024-08-19T16:37:18.000000Z",
		"deleted_at": null,
		"export_fields": "",
		"export_where": "",
		"integration_type": "0",
		"savedlist": "0",
		"mark_final_crc": "0",
		"show_alert": "31",
		"dbsync": "0",
		"binarycondition": "cc024934476d11eeafe90a62e8729021",
		"archived": "0",
		"archived_time": null,
		"campaign": {
			"camp_id": 433,
			"camp_name": "indianapolis",
			"trunkID": "3",
			"camp_channels": "0",
			"ivrid": "0",
			"amdivrid": "0",
			"phoneID": "0",
			"tenantid": "139",
			"groupid": "248",
			"camp_description": "",
			"active": "y",
			"started": "00:00:00",
			"camp_type": "CL",
			"ratio": "6:1",
			"status": "0",
			"inbound_number": "_cmp433$$",
			"queue_name": "q13931d430198891daf0",
			"maxretrys": "40",
			"waittime": "50",
			"callerid": "3174631720",
			"busyretrytime": "7200",
			"amdretrytime": "14400",
			"startdialing": "00:00:00",
			"stopdialing": "00:00:00",
			"afterhourroute": "",
			"busycb": "y",
			"amdCB": "y",
			"noanswercb": "y",
			"noansretrytime": "28800",
			"timezones": "n",
			"invalidcb": "y",
			"invalidretrytime": "28800",
			"urlcall": "https:\/\/remotep.callevo.net\/?PAGE=salesforce\/sales",
			"prepend": "1",
			"strip": "0",
			"dropcb": "y",
			"droptime": "14400",
			"customfield": "custom",
			"customlabel": "",
			"notifychannel": "",
			"notifytime": "30",
			"showcustomfield": "n",
			"notifyholding": "n",
			"forcedisposition": "n",
			"showdisp": "n",
			"defaultdisp": "0",
			"adaptive_dl_diff_target": "0",
			"adaptive_intensity": "17.00",
			"drop_limit": "3",
			"allow_inbound": "n",
			"agentcmp": "0",
			"calldataS": "<p><strong>Name:&nbsp;{lead_fname}&nbsp;{lead_mname}&nbsp;{lead_lname}<\/strong><\/p><p><strong>Address:&nbsp;{lead_address}&nbsp;<\/strong><\/p><p><strong>City:&nbsp;{lead_city}&nbsp;St:{lead_state}&nbsp;Zip:{lead_zip}<\/strong><\/p>",
			"calldataF": "",
			"callDataN": "",
			"inlinecallid": "y",
			"useautostart": "n",
			"buildrange": "",
			"minconnrate": "90",
			"demo": "0",
			"demoduration": "30",
			"democonnrate": "8",
			"fetcherwaittime": "1000",
			"brokenCB": "4",
			"linesdialed": "0",
			"talktime_alarm": "30",
			"talktime_color": "7382763",
			"timenoready": "20",
			"timenoready_color": "15536915",
			"timebreak": "30",
			"timebreak_color": "15887894",
			"timelunch": "30",
			"timelunch_color": "15780361",
			"timewrap": "15",
			"timewrap_color": "3407749",
			"goals": "0",
			"goalstype": "1",
			"expectedwaittime": "25",
			"waitingtime_alarm": "30",
			"waittime_color": "2208526",
			"detectmachine": "1",
			"initialrecordID": "0",
			"finalrecordID": "0",
			"agentammmessage": "0",
			"agentofflinemessage": "0",
			"pressonekey": "1",
			"linked_campaign": "0",
			"brokencallback": "4",
			"customquotes": "0",
			"recordcalls": "n",
			"tzscrubid": "3",
			"pepperclient": "callbacks",
			"sqlfilter": "",
			"timeother": "0",
			"timeother_color": "0",
			"timebathroom": "0",
			"timebathroom_color": "0",
			"timemeeting": "0",
			"timemeeting_color": "0",
			"ordertype": "2",
			"didrotation": "2",
			"smsnumber": "",
			"posturlcall": "",
			"qcenabled": "y",
			"usedncglobal": "y",
			"usecmpdnc": "y",
			"usecampdncfrom": "y",
			"calltimeid": "99",
			"qcurl": "",
			"integration_type": "4",
			"two_way_integration": "0",
			"activist_codes": "",
			"van_type": "0",
			"multinumber": "0",
			"alternate_numbers": "0",
			"recordings": "1",
			"sla": "60",
			"created_at": "2022-11-18 21:56:53",
			"updated_at": "2024-09-06 13:00:07",
			"deleted_at": null,
			"cps": "0",
			"logo": null,
			"logotype": null,
			"agentmessage": null,
			"show_alert": "7",
			"amdtransfer": "",
			"simulated": "0",
			"waitingrecordID": "0"
		},
		"pool_stats": {
			"pstatid": 937,
			"tenantid": "139",
			"camp_id": "433",
			"camp_name": "indianapolis",
			"poolid": "969",
			"poolname": "IX306B-3019Reverseskip-USEABLE.csv",
			"pooldate": "2023-05-11 13:44:28",
			"maxretrys": "9",
			"elegible": "0",
			"calling": "165",
			"nocalled": "3",
			"called": "15076",
			"CBtoday": "11470",
			"CBBeyond": "1455",
			"calledtoday": "0",
			"callfirsttime": "0",
			"exhausted": "233",
			"total": "15079",
			"penetration": "99.98",
			"priority": "0",
			"active": "0",
			"fetchingrecords": "20",
			"laststarted": "2024-08-14 18:32:18",
			"created_at": "2023-05-11 13:44:28",
			"updated_at": "2024-08-20 10:59:30",
			"lastreset": "2024-05-28 16:32:16",
			"passnumber": "32",
			"processing": "0",
			"avgtries": "5.4216",
			"tries": "32",
			"topprefix": [
				{
					"prefix": "317",
					"count": 13289,
					"percent": 88.13
				},
				{
					"prefix": "765",
					"count": 279,
					"percent": 1.85
				},
				{
					"prefix": "812",
					"count": 201,
					"percent": 1.33
				},
				{
					"prefix": "260",
					"count": 50,
					"percent": 0.33
				},
				{
					"prefix": "219",
					"count": 41,
					"percent": 0.27
				}
			]
		},
		"campaign_pool": {
			"cpoolid": 958,
			"camp_id": "433",
			"poolid": "969",
			"priority": "0",
			"fetched": "0",
			"lines": "15318",
			"imported": "15318",
			"errors": "0",
			"duplicated": "0",
			"scrups": "0",
			"stage": "",
			"ordertype": "5",
			"useprefix": "1",
			"fetchingrecords": "20",
			"tenantid": "139",
			"created_at": "2024-08-19 16:37:18",
			"updated_at": "2024-08-19 16:37:18"
		}
	},
	
}	
Devuelve el poolid activo para la camp
$app->get('/active_pool/{campid}', \App\Controllers\PoolController::class . ':getActivePool');
resultado
2234

Lista uno o mas registros 
$app->get('/campaignpools', \App\Controllers\PoolController::class . ':listCampaignPools')->setName('cmpPools');
$app->get('/campaignpool/{id}', \App\Controllers\PoolController::class . ':getCampaignPool');
[
	{
		"cpoolid": 1644,
		"camp_id": "425",
		"poolid": "1664",
		"priority": "100",
		"fetched": "0",
		"lines": "36",
		"imported": "36",
		"errors": "0",
		"duplicated": "0",
		"scrups": "0",
		"stage": "",
		"ordertype": "5",
		"useprefix": "1",
		"fetchingrecords": "20",
		"tenantid": "138",
		"created_at": "2024-06-21 15:05:16",
		"updated_at": "2024-06-21 15:05:16",
		"campaign": {
			"camp_id": 425,
			"camp_name": "camp-name-cl",
			"trunkID": "3",
			"camp_channels": "0",
			"ivrid": "0",
			"amdivrid": "0",
			"phoneID": "0",
			"tenantid": "138",
			"groupid": "162",
			"camp_description": "",
			"active": "y",
			"started": "00:00:00",
			"camp_type": "CL",
			"ratio": "3:1",
			"status": "0",
			"inbound_number": "_cmp425$$",
			"queue_name": "q1386e3a4a0156f23c96",
			"maxretrys": "9999",
			"waittime": "50",
			"callerid": "32423424234",
			"busyretrytime": "7200",
			"amdretrytime": "14400",
			"startdialing": "00:00:00",
			"stopdialing": "00:00:00",
			"afterhourroute": "",
			"busycb": "y",
			"amdCB": "y",
			"noanswercb": "y",
			"noansretrytime": "28800",
			"timezones": "n",
			"invalidcb": "y",
			"invalidretrytime": "28800",
			"urlcall": "https:\/\/remotep.callevo.net\/aws_survey?id=11",
			"prepend": "1",
			"strip": "0",
			"dropcb": "y",
			"droptime": "14400",
			"customfield": "custom",
			"customlabel": "",
			"notifychannel": "",
			"notifytime": "30",
			"showcustomfield": "n",
			"notifyholding": "n",
			"forcedisposition": "n",
			"showdisp": "n",
			"defaultdisp": "0",
			"adaptive_dl_diff_target": "0",
			"adaptive_intensity": "4.00",
			"drop_limit": "3",
			"allow_inbound": "n",
			"agentcmp": "0",
			"calldataS": "<p><strong>Name {lead_fname} {lead_mname} {lead_lname}<\/strong><\/p>",
			"calldataF": "",
			"callDataN": "",
			"inlinecallid": "y",
			"useautostart": "n",
			"buildrange": "",
			"minconnrate": "90",
			"demo": "0",
			"demoduration": "30",
			"democonnrate": "8",
			"fetcherwaittime": "1000",
			"brokenCB": "4",
			"linesdialed": "0",
			"talktime_alarm": "30",
			"talktime_color": "7382763",
			"timenoready": "20",
			"timenoready_color": "15536915",
			"timebreak": "30",
			"timebreak_color": "15887894",
			"timelunch": "30",
			"timelunch_color": "15780361",
			"timewrap": "15",
			"timewrap_color": "3407749",
			"goals": "0",
			"goalstype": "1",
			"expectedwaittime": "25",
			"waitingtime_alarm": "30",
			"waittime_color": "2208526",
			"detectmachine": "0",
			"initialrecordID": "0",
			"finalrecordID": "0",
			"agentammmessage": "0",
			"agentofflinemessage": "0",
			"pressonekey": "1",
			"linked_campaign": "0",
			"brokencallback": "4",
			"customquotes": "0",
			"recordcalls": "n",
			"tzscrubid": "3",
			"pepperclient": "callbacks",
			"sqlfilter": "AND custom9 != ''",
			"timeother": "0",
			"timeother_color": "0",
			"timebathroom": "0",
			"timebathroom_color": "0",
			"timemeeting": "0",
			"timemeeting_color": "0",
			"ordertype": "2",
			"didrotation": "1",
			"smsnumber": "",
			"posturlcall": "",
			"qcenabled": "y",
			"usedncglobal": "n",
			"usecmpdnc": "y",
			"usecampdncfrom": "y",
			"calltimeid": "99",
			"qcurl": "",
			"integration_type": "0",
			"two_way_integration": "0",
			"activist_codes": "",
			"van_type": "0",
			"multinumber": "0",
			"alternate_numbers": "0",
			"recordings": "1",
			"sla": "60",
			"created_at": "2022-10-20 14:08:08",
			"updated_at": "2024-10-01 11:00:07",
			"deleted_at": null,
			"cps": "0",
			"logo": "HC1LNM_logo_Image_2021-01-03_at_5.20.50_PM",
			"logotype": "jpeg",
			"agentmessage": null,
			"show_alert": "7",
			"amdtransfer": "",
			"simulated": "0",
			"waitingrecordID": "0"
		},
		"pool": {
			"poolid": 1664,
			"pooluploadname": "",
			"poolname": "JJSC_test_file3.csv",
			"poolfile": "JJSC_test_file3.csv",
			"pooldate": "2024-01-17 16:33:40",
			"firstline": "lead_fname,lead_lname,lead_phone,custom5,inlinecallid,lead_email,custom3",
			"totalrecords": "36",
			"dedupopts": "n",
			"errors": "0",
			"dbPool": "0",
			"odbc": "",
			"config": "",
			"prefixlen": "3",
			"randomize": "y",
			"listnumbers": "1,3,4,27,-1,56,5,25",
			"listline": "lead_fname,lead_lname,lead_phone,custom5,inlinecallid,lead_email,custom3",
			"sqlstring": null,
			"camp_id": "425",
			"FieldCond": "",
			"OperCond": "",
			"ValueCond": "",
			"CleanOld": "0",
			"tenantid": "138",
			"templateid": "503",
			"imported": "1",
			"startstop": "1",
			"created_at": "2024-01-17T16:33:40.000000Z",
			"updated_at": "2024-05-03T01:11:08.000000Z",
			"deleted_at": null,
			"export_fields": "",
			"export_where": "",
			"integration_type": "0",
			"savedlist": "0",
			"mark_final_crc": "0",
			"show_alert": "31",
			"dbsync": "0",
			"binarycondition": "",
			"archived": "0",
			"archived_time": null
		},
		"order_condition": {
			"ordertypeid": 5,
			"OrderName": "Attempts (only)",
			"orderfields": "order by reccalled, lead_id",
			"indexname": ""
		}
	},
	
]	

Lista los (files) pools con su relacion de camp
$app->get('/files', \App\Controllers\PoolController::class . ':listall')->setName('pools');

[
	{
		"poolid": 1664,
		"pooluploadname": "",
		"poolname": "JJSC_test_file3.csv",
		"poolfile": "JJSC_test_file3.csv",
		"pooldate": "2024-01-17 16:33:40",
		"firstline": "lead_fname,lead_lname,lead_phone,custom5,inlinecallid,lead_email,custom3",
		"totalrecords": "36",
		"dedupopts": "n",
		"errors": "0",
		"dbPool": "0",
		"odbc": "",
		"config": "",
		"prefixlen": "3",
		"randomize": "y",
		"listnumbers": "1,3,4,27,-1,56,5,25",
		"listline": "lead_fname,lead_lname,lead_phone,custom5,inlinecallid,lead_email,custom3",
		"sqlstring": null,
		"camp_id": "425",
		"FieldCond": "",
		"OperCond": "",
		"ValueCond": "",
		"CleanOld": "0",
		"tenantid": "138",
		"templateid": "503",
		"imported": "1",
		"startstop": "1",
		"created_at": "2024-01-17T16:33:40.000000Z",
		"updated_at": "2024-05-03T01:11:08.000000Z",
		"deleted_at": null,
		"export_fields": "",
		"export_where": "",
		"integration_type": "0",
		"savedlist": "0",
		"mark_final_crc": "0",
		"show_alert": "31",
		"dbsync": "0",
		"binarycondition": "",
		"archived": "0",
		"archived_time": null,
		"campaign": {
			"camp_id": 425,
			"camp_name": "camp-name-cl",
			"trunkID": "3",
			"camp_channels": "0",
			"ivrid": "0",
			"amdivrid": "0",
			"phoneID": "0",
			"tenantid": "138",
			"groupid": "162",
			"camp_description": "",
			"active": "y",
			"started": "00:00:00",
			"camp_type": "CL",
			"ratio": "3:1",
			"status": "0",
			.
		}
	},
	
]

Pool con todos los datos y relaciones
$app->get('/file/{poolid}', \App\Controllers\PoolController::class . ':getPool');
{
	"poolid": 1664,
	"pooluploadname": "",
	"poolname": "JJSC_test_file3.csv",
	"poolfile": "JJSC_test_file3.csv",
	"pooldate": "2024-01-17 16:33:40",
	"firstline": "lead_fname,lead_lname,lead_phone,custom5,inlinecallid,lead_email,custom3",
	"totalrecords": "36",
	"dedupopts": "n",
	"errors": "0",
	"dbPool": "0",
	"odbc": "",
	"config": "",
	"prefixlen": "3",
	"randomize": "y",
	"listnumbers": "1,3,4,27,-1,56,5,25",
	"listline": "lead_fname,lead_lname,lead_phone,custom5,inlinecallid,lead_email,custom3",
	"sqlstring": null,
	"camp_id": "425",
	"FieldCond": "",
	"OperCond": "",
	"ValueCond": "",

	"campaign": {
		"camp_id": 425,
		"camp_name": "camp-name-cl",
		"trunkID": "3",
		"camp_channels": "0",
		"ivrid": "0",
		"amdivrid": "0",
		"phoneID": "0",
		"tenantid": "138",
		"groupid": "162",
		"camp_description": "",
		.
	},
	"campaign_pool": {
		"cpoolid": 1644,
		"camp_id": "425",
		"poolid": "1664",
		"priority": "100",
		"fetched": "0",
		"lines": "36",
		"imported": "36",
		"errors": "0",
		"duplicated": "0",
		"scrups": "0",
		"stage": "",
		"ordertype": "5",
		"useprefix": "1",
		"fetchingrecords": "20",
		"tenantid": "138",
		"created_at": "2024-06-21 15:05:16",
		"updated_at": "2024-06-21 15:05:16"
	},
	"file_template": {
		"id": 503,
		"tenantid": "138",
		"template_name": "JJSC_test_file3.csv-template",
		"file_header": "lead_fname,lead_lname,lead_phone,custom5,conferencenum,inlinecallid,lead_email,custom3",
		"listline": "lead_fname,lead_lname,lead_phone,custom5,inlinecallid,lead_email,custom3",
		"listnumbers": "1,3,4,27,-1,56,5,25",
		"created_at": "2022-10-20T14:31:41.000000Z",
		"updated_at": "2022-10-20T14:31:57.000000Z",
		"deleted_at": null,
		"fields": [
			{
				"id": 6914,
				"field_name": "Lead Fname",
				"field_source": "lead_fname",
				"field_destination": "lead_fname",
				"file_template": "503",
				"created_at": "2022-10-20T14:31:41.000000Z",
				"updated_at": "2022-10-20T14:31:57.000000Z",
				"deleted_at": null
			},
			.
		]
	}
}

Pool abreviado
$app->get('/pool/{poolid}', \App\Controllers\PoolController::class . ':getPool');
{
	"poolid": 1664,
	"pooluploadname": "",
	"poolname": "JJSC_test_file3.csv",
	"poolfile": "JJSC_test_file3.csv",
	"pooldate": "2024-01-17 16:33:40",
	"firstline": "lead_fname,lead_lname,lead_phone,custom5,inlinecallid,lead_email,custom3",
	"totalrecords": "36",
	"dedupopts": "n",
	"camp_id": "425",
	"CleanOld": "0",
	"tenantid": "138",
	"templateid": "503",
	"imported": "1",
	"startstop": "1",
	"created_at": "2024-01-17T16:33:40.000000Z",
	"updated_at": "2024-05-03T01:11:08.000000Z",
	"dbsync": "0",
	"binarycondition": "",
	"archived": "0",
	"archived_time": null,
	"file_template": {
		"id": 503,
		"template_name": "JJSC_test_file3.csv-template",
		"file_header": "lead_fname,lead_lname,lead_phone,custom5,conferencenum,inlinecallid,lead_email,custom3",
		"created_at": "2022-10-20T14:31:41.000000Z",
		"updated_at": "2022-10-20T14:31:57.000000Z",
		"fields": [
			{
				"id": 6914,
				"field_name": "Lead Fname",
				"field_source": "lead_fname",
				"field_destination": "lead_fname",
				"created_at": "2022-10-20T14:31:41.000000Z",
				"updated_at": "2022-10-20T14:31:57.000000Z"
			},
			{
				"id": 6915,
				"field_name": "Lead Lname",
				"field_source": "lead_lname",
				"field_destination": "lead_lname",
				"created_at": "2022-10-20T14:31:41.000000Z",
				"updated_at": "2022-10-20T14:31:57.000000Z"
			},
			.
		]	
	}
}

Actualiza campaign pool
$app->put('/campaignpool[/{id}]', \App\Controllers\PoolController::class . ':updateCampaignPool');
Actualiza el objeto tal como se recibe en el request


Actualiza los datos de la camp
$app->put('/update_campaign_data[/{camp_id}]', \App\Controllers\CampaignController::class . ':updateCampaignData');
CALL updatecampaigndata(:camp_id)

Actualiza los datos del pool
$app->put('/update_pool_data[/{pool_id}]', \App\Controllers\PoolController::class . ':updatePoolData');
CALL updatepooldata(:camp_id, :poolid)

// Reset status and dispositions and count
Resetea segun tabs
$app->put('/pool/reset/{id}', \App\Controllers\PoolController::class . ':reset');
 {
    "tabName": "status",
    "status_2": "noa",
    "status_3": "busy",
    "status_5": "dropped",
    "status_6": "amd",
    "status_7": "fax"
}
Realiza la operacion de conteo segun disp
$app->put('/pool/dispcount/{id}', \App\Controllers\PoolController::class . ':reset');
 {
    "noa" : 12345
    "busy" : 12345
    "dropped" : 12345
    "amd" : 12345
    "fax : 12345
}


/**
* ========================= ROUTING ==============================
*/
Lista uno mas phones
$app->get('/phones', \App\Controllers\PhoneController::class . ':listall');
$app->get('/phones/{state}/{ratecenter}', \App\Controllers\PhoneController::class . ':listall');
$app->get('/phone/{id}', \App\Controllers\PhoneController::class . ':getPhone');
[
	{
		"phoneid": 8,
		"groupid": "1",
		"phone": "7207388397",
		"ptypeid": "3",
		"description": "Inbound Test Number",
		"taken": "n",
		"tenantid": "86",
		"active": "1",
		"calls": "103",
		"prefixid": "196",
		"stateid": "7",
		"ratecenter": "",
		"flagged": "0",
		"flag_result": "",
		"created_at": null,
		"updated_at": "2021-12-09 16:52:05",
		"deleted_at": null,
		"phoneid_fk": null,
		"phone_type": null
	},
	
]

Agrega/modifica un phone
$app->post('/phone', \App\Controllers\PhoneController::class . ':modifyPhone');
$app->put('/phone', \App\Controllers\PhoneController::class . ':modifyPhone');
 {
    "phoneid": "-1",
    "phone": "9434693411",
    "ptypeid": "1",
    "description": "A_OK",
    "tenantid": "98",
    "active": "0",
    "prefixid": "389",
    "stateid": "13",
    "ratecenter": "",
    "groupid": "91",
    "userid": "436",
    "flagged": "0"
}

Borra un phone por ID
$app->delete('/phone/{id}', \App\Controllers\PhoneController::class . ':deletePhone');


$app->put('/activephone', \App\Controllers\PhoneController::class . ':activePhone');
entrada
{
	id: ids,
	valactive: valactive,
	userid: "{{ auth.user.userid }}"
},
salida
{
	"status": "ok",
	"message": {
		"records": 3
	}
}

/*
Saul Diaz — 08/22 at 12:25 PM
@jjsc si recibes esto buscas el number en phones  en flagged pones 1 y en flag_result result pones el valor
*/
$app->get('/600reject', \App\Controllers\PhoneController::class . ':_600reject');
entrada
{
	"num" : 11233344455,
	"callid": 12313123,
	"result": 608,
	"server": ""
}

Lista
$app->get('/trunks', \App\Controllers\TrunkController::class . ':listall');
$app->get('/trunk/{id}', \App\Controllers\TrunkController::class . ':getTrunk');
salida
[
	{
		"trunkID": 3,
		"tenantid": "25",
		"name": "callevo",
		"tech": "SIP",
		"path": "callevo",
		"description": "Default admin ",
		"num_channels": "20"
	}
]

Agrega/modifica 
$app->post('/trunk', \App\Controllers\TrunkController::class . ':modifyTrunk');
$app->put('/trunk', \App\Controllers\TrunkController::class . ':modifyTrunk');
entrada
{
	"trunkID": 3,
	"tenantid": "25",
	"name": "callevo",
	"tech": "SIP",
	"path": "callevo",
	"description": "Default admin ",
	"num_channels": "20"
}

Borra por id
$app->delete('/trunk/{id}', \App\Controllers\TrunkController::class . ':deleteTrunk');


Lista 
$app->get('/inRoutes', \App\Controllers\InRouteController::class . ':listall');
$app->get('/inRoute/{id}', \App\Controllers\InRouteController::class . ':getInRoute');
salida
[
	{
		"inrouteid": 79,
		"phoneID": "7572",
		"ivrid": "229",
		"tenantid": "138",
		"context": "internal",
		"phone": null,
		"ivr": {
			"ivrid": 229,
			"tenantid": "138",
			"ivrname": "test_ivr",
			"enablekeys": "n"
		}
	}
]

Agrega/modifca
$app->post('/inRoute', \App\Controllers\InRouteController::class . ':modifyInRoute');
$app->put('/inRoute', \App\Controllers\InRouteController::class . ':modifyInRoute');
 {
    "inrouteid": "-1",
    "phoneID": "7572",
    "ivrid": "229",
    "context": "internal"
}

Borra por ID
$app->delete('/inRoute/{id}', \App\Controllers\InRouteController::class . ':deleteInRoute');

// no se esta usando
$app->get('/routes', \App\Controllers\RouteController::class . ':listall');
$app->get('/route/{id}', \App\Controllers\RouteController::class . ':getRoute');
$app->post('/route', \App\Controllers\RouteController::class . ':modifyRoute');
$app->put('/route', \App\Controllers\RouteController::class . ':modifyRoute');
$app->delete('/route/{id}', \App\Controllers\RouteController::class . ':deleteRoute');


/**
* ========================= RECORDING ==============================
*/
$app->get('/playfile/{lang}/{name}', \App\Controllers\RecordingController::class . ':getPlayfile');
devuelve un file content-transfer-encoding binary y content-type audio/gsm 

$app->get('/recording_download/{id}[/{phone}]', \App\Controllers\RecordingController::class . ':getRecordingDownload');	
Devuelve si el call recording para el call id existe en el s3

Chequea si existe o no el recording 
$app->get('/recording_exists/{id}', \App\Controllers\RecordingController::class . ':getRecordingDownload');
{
	"type": "INFO",
	"message": "Ok",
	"more": "2024\/10\/01\/louisville_434_20241001161002_5025335938_70245764_26313124_ip-172-30-11-103-ec2-internal-1727798981-1522.mp3"
}

devuelve el url correspondiente para reproducir el recording (antigua)
$app->get('/recording_url/{callid}', \App\Controllers\RecordingController::class . ':getRecordingUrl');
https://ip.callevo.com/public/recording_download/70245764 


/**
* ========================= ASTERISK RECORDING ==============================
*/
Devuelve uno o mas asterisk recording
$app->get('/recordings', \App\Controllers\RecordingController::class . ':listall');
$app->get('/recording/{id}', \App\Controllers\RecordingController::class . ':getRecording');
[
	{
		"recID": 21,
		"tenantid": "139",
		"recName": "MCO Offer",
		"recfilename": "mco_offer_12",
		"recfillename_type": "gsm",
		"recfilename_ext": "gsm",
		"used": "y"
	},
	{
		"recID": 22,
		"tenantid": "139",
		"recName": "\tcinci",
		"recfilename": "cinci.gsm",
		"recfillename_type": "gsm",
		"recfilename_ext": "gsm",
		"used": "y"
	},
	.
]

Agrega/modifica asterisk recording, en el filecontent va el file en base64 y este se almacenará en el s3
$app->post('/recording', \App\Controllers\RecordingController::class . ':modifyRecording');
$app->put('/recording', \App\Controllers\RecordingController::class . ':modifyRecording');
entrada
{
	"recName" : $data['recName'],
	"recfilename" : $basename,
	"recfillename_type" : $data['recfilename_type'],
	"recfilename_ext" : $data['recfilename_ext'],
	"filecontent" : "sdfasdfadfadf"
	"used" : $data['used'],
}

Borra un asterisk recording de la db y del s3
$app->delete('/recording/{id}', \App\Controllers\RecordingController::class . ':deleteRecording');


// MOH (funciones antiguas que trabajan directamente con el directorio de asterisk)
$app->get('/mohs', \App\Controllers\MusicOnHoldController::class . ':listall');
$app->get('/moh/{id}', \App\Controllers\MusicOnHoldController::class . ':getMusicOnHold');
$app->post('/moh', \App\Controllers\MusicOnHoldController::class . ':modifyMusicOnHold');
$app->put('/moh', \App\Controllers\MusicOnHoldController::class . ':modifyMusicOnHold');
$app->delete('/moh/{id}', \App\Controllers\MusicOnHoldController::class . ':deleteMusicOnHold');

/**
* ========================= IVR ==============================
*/
Lista uno mas IVR
$app->get('/ivrs', \App\Controllers\IvrController::class . ':listall'); 
[
	{
		"ivrid": 206,
		"tenantid": "139",
		"ivrname": "Inbound",
		"enablekeys": "n",
		"ivr_steps": [
			{
				"ivrstepid": 582,
				"ivrid": "206",
				"optionid": "1",
				"priority": "5",
				"parameter1": "",
				"parameter2": "",
				"parameter3": ""
			},
			{
				"ivrstepid": 578,
				"ivrid": "206",
				"optionid": "6",
				"priority": "1",
				"parameter1": "",
				"parameter2": "",
				"parameter3": ""
			},
.
		],
		"ivr_keys": []
	},
	{
		"ivrid": 207,
		"tenantid": "139",
		"ivrname": "inbound after hours",
		"enablekeys": "n",
		"ivr_steps": [
			{
				"ivrstepid": 585,
				"ivrid": "207",
				"optionid": "1",
				"priority": "3",
				"parameter1": "",
				"parameter2": "",
				"parameter3": ""
			},
			{
				"ivrstepid": 583,
				"ivrid": "207",
				"optionid": "6",
				"priority": "1",
				"parameter1": "",
				"parameter2": "",
				"parameter3": ""
			},
			{
				"ivrstepid": 584,
				"ivrid": "207",
				"optionid": "55",
				"priority": "2",
				"parameter1": "Local\/3179535788",
				"parameter2": " ",
				"parameter3": ""
			}
		],
		"ivr_keys": []
	},
	
]	
$app->get('/ivr/{id}', \App\Controllers\IvrController::class . ':getIvr');
{
	"status": "ok",
	"message": [
		{
			"ivrid": 111,
			"tenantid": "86",
			"ivrname": "ivrGen-testsborjacl",
			"enablekeys": "n",
			"ivr_steps": [
				{
					"ivrstepid": 324,
					"ivrid": "111",
					"optionid": "1",
					"priority": "5",
					"parameter1": "",
					"parameter2": "",
					"parameter3": ""
				},
				{
					"ivrstepid": 319,
					"ivrid": "111",
					"optionid": "6",
					"priority": "1",
					"parameter1": "",
					"parameter2": "",
					"parameter3": ""
				},
				{
					"ivrstepid": 321,
					"ivrid": "111",
					"optionid": "44",
					"priority": "2",
					"parameter1": "ivrAMD-testsborjacl",
					"parameter2": "",
					"parameter3": ""
				},
				{
					"ivrstepid": 323,
					"ivrid": "111",
					"optionid": "54",
					"priority": "4",
					"parameter1": "13",
					"parameter2": "3",
					"parameter3": ""
				},
				{
					"ivrstepid": 322,
					"ivrid": "111",
					"optionid": "69",
					"priority": "3",
					"parameter1": "",
					"parameter2": "",
					"parameter3": ""
				}
			]
		}
	]
}

Agrega/modifica
$app->post('/ivr', \App\Controllers\IvrController::class . ':modifyIvr');
$app->put('/ivr[/{id}]', \App\Controllers\IvrController::class . ':modifyIvr');
{
    "ivrid": -1,
    "ivrname": "New IVR",
    "ivrsteps": [
        {
            "optionid": 6,
            "priority": 1,
            "parameter1": "",
            "parameter2": "",
            "parameter3": ""
        },
        {
            "optionid": 58,
            "priority": 2,
            "parameter1": "",
            "parameter2": "",
            "parameter3": ""
        },
      
    ],
    "enablekeys": "y",
    "ivrkeys": [
        {
            "ivrkeyid": -1,
            "ivrid": -1,
            "keystroke": "0",
            "optionid": "6",
            "parameter1": "",
            "parameter2": "",
            "parameter3": ""
        },
 
    ],
    "force_gen_ivr": "n"
}

Borra por ID
$app->delete('/ivr/{id}', \App\Controllers\IvrController::class . ':deleteIvr');

$app->get('/ivr_cmds', \App\Controllers\IvrController::class . ':getIvrCommands');


/*
* =============== NEW AGENT ===========================
*/
Agrega en agentcmpsession al agente
$app->get('/newagent/login', \App\Controllers\AgentController::class . ':addLoginCamp');
https://apidev.callevo.net/api/public/newagent/login?userID=u251521119c5bf9249ca&tenantID=138&agentID=828&camp_id=-1
salida
{
	"status": "OK",
	"action": "ADDLOGIN",
	"answer": "OK"
}

Lista las camp del agente
$app->get('/newagent/cmp', \App\Controllers\AgentController::class . ':getAgentCmp');
https://apidev.callevo.net/api/public/newagent/cmp?userID=u251521119c5bf9249ca&tenantID=138&agentID=828
[
	{
		"camp_id": "425",
		"camp_name": "camp-name-cl",
		"team": "q1386e3a4a0156f23c96",
		"isselected": "false"
	},
	{
		"camp_id": "889",
		"camp_name": "jjsccampcl1",
		"team": "q138c7d347f1fdbf320e",
		"isselected": "false"
	}
]

Lista camp manuales
$app->get('/newagent/get_campaigns', \App\Controllers\CampaignController::class . ':getCampaigns');
https://apidev.callevo.net/api/public/newagent/get_campaigns?userID=u251521119c5bf9249ca&tenantID=138&agentID=828
[
	{
		"camp_name": "camp-name-cl",
		"camp_id": 425
	},
	{
		"camp_name": "jjsccampcl1",
		"camp_id": 889
	}
]

Lista camp <> CL
$app->get('/newagent/transfer_campaign/{tenantid}', \App\Controllers\CampaignController::class . ':transferCampaigns');
[
	{
		"camp_name": "camp-name-cl",
		"camp_id": "425"
	},
	{
		"camp_name": "jjsccampcl1",
		"camp_id": "889"
	}
]

$app->get('/newagent/get_disposition', \App\Controllers\DispositionController::class . ':getDispositionCampaign');
https://apidev.callevo.net/api/public/newagent/get_disposition?camp_id=425
[
	{
		"dispid": "2380",
		"statusid": "6",
		"dispcode": "AMM",
		"dispdesc": "Answering machine (agent detected)",
		"success": "n",
		"contact": "n",
		"presentation": "n",
		"dnc": "n",
		"enabled": "y",
		"finalcrc": "n",
		"recall": "y",
		"recallscale": "0",
		"seconds": "14400",
		"rollover": "n",
		"rocamp_id": "0",
		"revenue": "0.00",
		"crcid": "0",
		"tenantid": "138",
		"created_at": "2022-10-19 14:39:08",
		"updated_at": "2022-10-19 14:39:08",
		"deleted_at": null,
		"vanresultid": "0",
		"integration_type": "0",
		"dcid": "13689",
		"camp_id": "425",
		"clientcode": "",
		"qcenabled": "n"
	},
	{
		"dispid": "2382",
		"statusid": "1",
		"dispcode": "BAD",
		"dispdesc": "Bad number",
		"success": "n",
		"contact": "n",
		"presentation": "n",
		"dnc": "n",
		"enabled": "y",
		"finalcrc": "y",
		"recall": "n",
		"recallscale": "0",
		"seconds": "0",
		"rollover": "n",
		"rocamp_id": "0",
		"revenue": "0.00",
		"crcid": "0",
		"tenantid": "138",
		"created_at": "2022-10-19 14:39:08",
		"updated_at": "2022-10-19 14:39:08",
		"deleted_at": null,
		"vanresultid": "0",
		"integration_type": "0",
		"dcid": "13691",
		"camp_id": "425",
		"clientcode": "",
		"qcenabled": "n"
	},
	
]	

$app->get('/newagent/transfer_agents/{tenantid}', \App\Controllers\AgentController::class . ':getTransferAgent');
https://apidev.callevo.net/api/public/newagent/transfer_agents/138
[
	{
		"data": "828",
		"label": "JJSc tenant test agent"
	},
	{
		"data": "828",
		"label": "JJSc tenant test agent"
	}
]

Devuelve al objeto completo de user verificando el passwd contra el hashed
$app->get('/auth', \App\Controllers\AgentController::class . ':getAuth');
https://apidev.callevo.net/api/public/auth?userID=u251521119c5bf9249ca&password=s6P7v4K1
{
	"userid": 844,
	"tenantid": "138",
	"usertype": "27",
	"username": "u251521119c5bf9249ca",
	"pass": "s6P7v4K1",
	"language": "en",
	"fullname": "JJSc tenant test agent",
	"email_verified": "1",
	"email": "jsainz@callevo.com",
	"logged": "n",
	"stamp": "2024-10-02 19:21:50",
	"clientaccess": "0",
	"phone_number": "",
	"maxchannels": "200",
	"hashed": "$2y$10$HGkst.WeaJjv\/s3k3sxhm.DbqrtnqhwiV0TqG005Up95fslil1tmq",
	"refresh_token": "eyJjdHkiOiJKV1QiLCJlbmMiOiJBMjU2R0NNIiwiYWxnIjoiUlNBLU9BRVAifQ.g1kacCDLNNoCNT1XD5BBimx3QE8a5qq6xzKBLb6jqDH1V02ctRTtFUHvg11yzCvWdsdJ0O23WlwqyGyvgM7wfNi4s9sPtoYQHe8V5bCwA7xQtJnUAyRsYp3Pa9NDyKNVc87y9MA-zx1siwmuiJCJNcI8vEOJ8J9B8QWzFNj4bNQh5sRFQ-GnQn-awqEZFIJsEkEgOt6904AoWOGLPwQH1AGifIgs85jUiNEgC4AqFj6Ftc7z5WIJFXioqMegbBLV21bEUUOE3lqTtjN1MoE4CSto5RGwWUzHnlUY9-PLfr4_qXM9-vsN0vt3z2KSzkJuahtasxpF-2DRrXmVLY010w.Ib5JMfgfZExDgQGv.ssxgX-9jNjdWjhbNu6v0FccrkT3sOPctOMJxfsXAYQbzH4nw9TummF5k7t-4XiqO3w57f36JXjhNEQ0Bxxlbcq8rhgqDMqOiUH9llANvparW3Pe9ycAPt8LhjEmf0mtnsafrKl5WZXqgDMSyZSbAvIfk9-lO6dr-h8NIOqRQf-oflC-NOMGpupJuGZ5ByoukVphyVILW87xoCdlxnr6pjL41EIC9odYVqi8z9PfpOqcHeM230lOO-8KuX2DbpqhNV1MRQeNHH32iHI9myGyCucpMHp5BBJe4ivWz8U-AvqiUDoDgh_9jcBXkfweDpuXborpyGl1a4dI0Dj3RrtctEOiniGDrWwYFO32MT22be2vlIYbDxEceT8IZCz8coDz-LeWzwY9cp-VakzCn6G_ERdGynKDNMObdDQydEB21f9Ju-yr7MCKPXcL82TFh1d7JxceRRT6-dXWDPwamewT6HVPjD7ebjN9FPM-SdqY2rLW8nwiAjFWQ51CjQ7xaguTYhOb5MotAY8jKIgQtwscuI5fFZRAZnKSmoaqTlRC1A-Iz6FbYn_Qm5JuKyo53VDwLGeflWqouGNRxBDMySKe_DjhNvqxiFWnWHAYAN1HReQLwAArSyGFgWl4Wkm9WouYfcQiJ2OIyoGsjy6qIVq5tSiBOsbT0P9myrtN286xXyiBEMA8ujcBoUxCUih2tc0zoc0i02IW3SQXoQgvRu3-0aBNrfGR1ZcZejDvcGCWD8ig4g_PC5IisC_zf4dd0QV-sKq_lVCNnicvcakIA4iy6KmGDhhwwcdsGk_8C6wGu0smz2GwVmlkXnnqam22p5SId27Fdi5dejXUGFTc9EP3AC4iRbT4pO5CDf8Rqodpr5_p_LurqWjHo8t5wsPrwTV439GyCKhQIsiOLcfSvXV92g-rZYYsKTd2Qpm4UdUlLKK5J-cYb1gdhISStS5nLRE_-fnRAWdxuzrhP_JKEIEFN08zcfzb6est-NfSwq1XlKyLRQ5PXiISqVNqqPE6b1loX_5LCMz4dzoHGTgNlkajriZNYM_1-2k0CkZvQEYv-w3QLEkNMO1hf5OMNIEL4XOdpWHNKthEp4eLbzDe_rClqnEp2-wOgX6xDHwnGzN6daIyK-lKvQmU8MRg3lS0TwUFJjeF9a6I5zXIzv26ZkuuiEwG6rjcRhBr3LVHIDa6gkpGpv7yMalh19RdtLAgU-3XgYOXB7XrbLc6x8fk2zWu2aq6T2eZHQJESdARVuWdPnHbYGROlvG_5fdwLklUzbYizhAb8fgECfFI-Urer2mnkuPXwrEBD7NclGA.LIpz-NuhngAJ195wYcnvPQ",
	"created_at": "2022-10-19T20:33:40.000000Z",
	"updated_at": "2024-10-02T19:21:50.000000Z",
	"deleted_at": null,
	"idtoken": "eyJraWQiOiJnVTVhMEUxUW95bGVtaFwvWE8xc3hjMHQ0NEFobXkzVktoUzZ0eGlPb080dz0iLCJhbGciOiJSUzI1NiJ9.eyJzdWIiOiIxMGMzNWIyYi00ZmM2LTQ3NTMtYjY4My1kOWViYjIwODQ0NDAiLCJlbWFpbF92ZXJpZmllZCI6dHJ1ZSwiaXNzIjoiaHR0cHM6XC9cL2NvZ25pdG8taWRwLnVzLWVhc3QtMS5hbWF6b25hd3MuY29tXC91cy1lYXN0LTFfN25INzZQQWFTIiwiY29nbml0bzp1c2VybmFtZSI6InUyNTE1MjExMTljNWJmOTI0OWNhIiwib3JpZ2luX2p0aSI6IjFmZjA0ZGI1LTYxMDUtNGFjZS05YzE5LTUyNDAyYmM0NzUxYiIsImF1ZCI6Ijc1N2UydnY1NXNsdW5oMDlyNTRqdTM1Z2U3IiwiZXZlbnRfaWQiOiJlMmY0NzNkZC02YjZkLTQ1NTktOTIzOS0zYmRiNzFjY2YxNDYiLCJ1cGRhdGVkX2F0IjoxNzA0Mzc5ODIxLCJ0b2tlbl91c2UiOiJpZCIsImF1dGhfdGltZSI6MTcyNzg4MDQ4MCwibmFtZSI6IkpKU2MgdGVuYW50IHRlc3QgYWdlbnQiLCJleHAiOjE3Mjc5NjY4ODAsImlhdCI6MTcyNzg4MDQ4MCwianRpIjoiYTg5NzFhM2MtNWRmOC00ZDQ1LWE4NGYtNDI0NWRjYWY4NWVjIiwiZW1haWwiOiJqc2FpbnpAY2FsbGV2by5jb20ifQ.S9pscByC9QrQtrl-Uwsjlya7mZE4NyBeKNdCUFshzcz3qmC1dXcVt6bd3ofnb5q1xkGN1u5xQIQN0B9vPHBAdAmsdcgiCVCpQbQ2hpEi81n54npA8rjRCSUj6bDeFgn4CQHOTgTQWujhYQogUmaVsywIusPtv3EUKEoWoQWncOYVb5E0nrCaanyiTBuhg9P_nU7YDYACrP3yDCNNzxoyjJWTkLBHhmqW36sdR5SN24TytAS-K2l-cbQH84mKUHMkkTr_v3RLdjSoKCG2go0Zozo6qonPS5gFfdLEeRJ3WMaLagC1G8r99idQrU5WQNYw4hK8x52MP0S_WFw2fNm27Q",
	"lastlogin": "2024-10-02 14:21:50",
	"Token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzUxMiJ9.eyJ0ZW5hbnRpZCI6IjEzOCIsInVzZXJpZCI6ODQ0LCJ1c2VydHlwZSI6IjI3Iiwic2NvcGUiOlsicmVhZCJdLCJleHBpcmUiOjE3Mjc5MDk5NDYsImlhdCI6MTcyNzkwNjM0Nn0.yTFBlEwyC1h0GHwmqciiIxSxQzqKIaG8e1tx4DHQmRzO7KsC5exlaNc69ZIaKnK_NUqNfjQwW0He8_yshs8JbA",
	"Teams": [
		{
			"memberid": 40067,
			"queueid": "1006",
			"uniqueid": "0",
			"queue_name": "q138c7d347f1fdbf320e",
			"agentid": "828",
			"interface": "Agent\/u251521119c5bf9249ca",
			"penalty": "0",
			"callstaken": "0",
			"status": "LOGOFF",
			"lastcall": "0",
			"paused": "0",
			"manager": "n",
			"membername": "",
			"calls": "0",
			"announce_holdtime": "no",
			"wrapuptime": "0",
			"camp_id": "0",
			"lead_id": "0",
			"callid": "0",
			"channelid": "",
			"created_at": "2024-01-17 16:57:43",
			"updated_at": "2024-01-17 16:57:43",
			"deleted_at": null
		},
		{
			"memberid": 40068,
			"queueid": "1005",
			"uniqueid": "0",
			"queue_name": "q1386e3a4a0156f23c96",
			"agentid": "828",
			"interface": "Agent\/u251521119c5bf9249ca",
			"penalty": "0",
			"callstaken": "0",
			"status": "LOGOFF",
			"lastcall": "0",
			"paused": "0",
			"manager": "n",
			"membername": "",
			"calls": "0",
			"announce_holdtime": "no",
			"wrapuptime": "0",
			"camp_id": "0",
			"lead_id": "0",
			"callid": "0",
			"channelid": "",
			"created_at": "2024-01-17 16:57:43",
			"updated_at": "2024-01-17 16:57:43",
			"deleted_at": null
		},
		{
			"memberid": 40069,
			"queueid": "2166",
			"uniqueid": "0",
			"queue_name": "q1380cc7efc812381f69",
			"agentid": "828",
			"interface": "Agent\/u251521119c5bf9249ca",
			"penalty": "0",
			"callstaken": "0",
			"status": "LOGOFF",
			"lastcall": "0",
			"paused": "0",
			"manager": "n",
			"membername": "",
			"calls": "0",
			"announce_holdtime": "no",
			"wrapuptime": "0",
			"camp_id": "0",
			"lead_id": "0",
			"callid": "0",
			"channelid": "",
			"created_at": "2024-01-17 16:57:43",
			"updated_at": "2024-01-17 16:57:43",
			"deleted_at": null
		}
	],
	"agent": {
		"agentid": 828,
		"onHold": "0",
		"agent_code": "u251521119c5bf9249ca",
		"name": "JJSc tenant test agent",
		"autologoff": "15",
		"ackcall": "no",
		"wrapuptime": "0",
		"musiconhold": "agents",
		"updatecdr": "yes",
		"group": "",
		"recordagentcalls": "",
		"recordformat": "wav",
		"createlink": "yes",
		"urlprefix": "",
		"savecallsin": "",
		"custom_beep": "beep",
		"status": "LOGOFF",
		"statustime1": "2022-10-19 20:33:40",
		"tenantid": "138",
		"queue_name": "",
		"uniqueid": "0",
		"call_uniqueid": "",
		"loginstart": "0",
		"lastcall": "0",
		"paused": "0",
		"lasttime": null,
		"callid": "0",
		"loginunique": "",
		"holdchannel": "",
		"urllogin": "",
		"logintype": "GET",
		"urllogout": "",
		"logouttype": "GET",
		"urlbtwcalls": "",
		"btwcallstype": "GET",
		"gotoready": "n",
		"userid": "844",
		"_ROLES": "",
		"token": "",
		"callswaiting": "0",
		"clientversion": "",
		"latency": "0",
		"sqldelay": "0",
		"selectleaddelay": "0",
		"uuid": "",
		"agent_message": "",
		"deleted_at": null,
		"created_at": null,
		"updated_at": null,
		"Password": "s6P7v4K1"
	},
	"user_type": {
		"usertype": 27,
		"descripcion": "Agent",
		"newhomepage": "0",
		"homepage": "none",
		"can_create": "0",
		"scopes": "read",
		"showinadmin": "0",
		"created_at": "2018-08-03T05:05:47.000000Z",
		"updated_at": "2023-02-27T18:20:11.000000Z",
		"deleted_at": null,
		"roles": []
	}
}
o error si esta mal el passwd
[
	{
		"message": "ERROR invalid password"
	}
]

/**
* ========================= STATES ==============================
*/
$app->get('/states', \App\Controllers\StateController::class . ':listall')->setName('states');
$app->get('/state/{id}', \App\Controllers\StateController::class . ':getState');
{
	"status": "ok",
	"message": {
		"AK": "Alaska",
		"AL": "Alabama",
		"AR": "Arkansas",
		"AS": "American Samoa",
		"AZ": "Arizona",
		"CA": "California",
		"CO": "Colorado",
		"CT": "Connecticut",
		"DC": "District of Columbia",
		"DE": "Delaware",
		"FL": "Florida",
		"FM": "Federated States of Micronesia",
		"GA": "Georgia",
		"GU": "Guam",
		"HI": "Hawaii",
		"IA": "Iowa",
 
    }
}	
Agrega/modifica 
$app->post('/state', \App\Controllers\StateController::class . ':modifyState');
$app->put('/state', \App\Controllers\StateController::class . ':modifyState');
{
   "state_abr" : $data['state_abr'],
   "state_name" : $data['state_name'],
}

Borra
$app->delete('/state/{id}', \App\Controllers\StateController::class . ':deleteState');

/**
* ========================= USERS TYPES ==============================
*/
Listado con su relacion de roles
$app->get('/users_type', \App\Controllers\UserTypeController::class . ':index')->setName('users_type');
[
	{
		"usertype": 1,
		"descripcion": "System Administrator",
		"homepage": "performance",
		"can_create": "1",
		"scopes": "read|write|delete",
		"showinadmin": "1",
		"created_at": "2018-08-03T05:05:47.000000Z",
		"updated_at": "2018-08-08T10:09:20.000000Z",
		"deleted_at": null,
		"roles": [
			{
				"id": 17,
				"name": "performance",
				"permissions": "read,write,delete",
				"roles_order": "10",
				"admin_type": "1",
				"created_at": "2018-05-05T11:17:49.000000Z",
				"updated_at": "2018-05-05T11:17:49.000000Z",
				"pivot": {
					"usertype": "1",
					"role_id": "17"
				}
			},
			
		],
	}
.
]

Listado abreviado	
$app->get('/user_types_list', \App\Controllers\UserTypeController::class . ':listUserTypes');
[
	{
		"usertype": 27,
		"descripcion": "Agent",
		"homepage": "none",
		"scopes": "read"
	},
	{
		"usertype": 2,
		"descripcion": "Callevo",
		"homepage": "tenants",
		"scopes": "read|write|delete"
	},
	
]

Recupera un type	
$app->get('/user_type/{typeid}', \App\Controllers\UserTypeController::class . ':getype');
[
	{
		"usertype": 27,
		"descripcion": "Agent",
		"newhomepage": "0",
		"homepage": "none",
		"can_create": "0",
		"scopes": "read",
		"showinadmin": "0",
		"created_at": "2018-08-03T05:05:47.000000Z",
		"updated_at": "2023-02-27T18:20:11.000000Z",
		"deleted_at": null,
		"roles": []
	}
]

Agrega/modifica
$app->post('/usertype', \App\Controllers\UserTypeController::class . ':modifyUserType');
$app->put('/usertype', \App\Controllers\UserTypeController::class . ':modifyUserType');
{
	"usertype": 27,
	"descripcion": "Agent",
	"newhomepage": "0",
	"homepage": "none",
	"can_create": "0",
	"scopes": "read",
	"showinadmin": "0",
}		

Borra 
$app->delete('/usertype/{id}', \App\Controllers\UserTypeController::class . ':deleteUserType');


/**
* ========================= ROLES ==============================
*/
Lista roles
$app->get('/roles', \App\Controllers\RoleController::class . ':listall')->setName('roles');
[
	{
		"id": 1,
		"name": "rsalesviewer",
		"permissions": "read",
		"roles_order": "99",
		"admin_type": "1",
		"created_at": "2018-04-17T02:46:57.000000Z",
		"updated_at": "2018-04-17T02:46:57.000000Z"
	},
	{
		"id": 2,
		"name": "ragentsviewer",
		"permissions": "read",
		"roles_order": "99",
		"admin_type": "1",
		"created_at": "2018-04-17T02:48:51.000000Z",
		"updated_at": "2018-04-17T02:48:51.000000Z"
	},
	
]	

Recupera 1
$app->get('/role/{id}', \App\Controllers\RoleController::class . ':getRole');
[
	{
		"id": 2,
		"name": "ragentsviewer",
		"permissions": "read",
		"roles_order": "99",
		"admin_type": "1",
		"created_at": "2018-04-17T02:48:51.000000Z",
		"updated_at": "2018-04-17T02:48:51.000000Z"
	}
]

Agrega/modifica 
$app->post('/role', \App\Controllers\RoleController::class . ':modifyRole');
$app->put('/role', \App\Controllers\RoleController::class . ':modifyRole');
{
	"name": "ragentsviewer",
	"permissions": "read",
}

Borra 
$app->delete('/role/{id}', \App\Controllers\RoleController::class . ':deleteRole');


/**
* ========================= LOGO ==============================
*/
Recupera un logo en formato html data image inline
$app->get('/logo/{id}/{tenantid}', \App\Controllers\ConfigController::class . ':getLogo');
{
	"status": "ok",
	"message": "data:image\/jpeg;base64,\/9j\/4AAQSkZJRgABAQAAAQABAAD\/2wBDAAMCAgICAgMCAg"
}

Agerga/modifica un logo, filecontent en base64
$app->post('/logo', \App\Controllers\ConfigController::class . ':modifyLogo');
$app->put('/logo', \App\Controllers\ConfigController::class . ':modifyLogo');
{
	
	"logo":"icono primero con espacios.png",
	"camp_id":"425",
	"filecontent":"iVBORw0KGgoAAAANSUhEUgAAADIA."
}		

Borra
$app->delete('/logo/{id}/{tenantid}', \App\Controllers\ConfigController::class . ':deleteLogo');


# RANGE/PAGINATIONS 

Lista user paginados

`ADMIN => ` Su uso esta en el screen users para listar todos los usuarios, eliminados o no

```php
$app->post('/users_range', \App\Controllers\UserController::class . ':getUsersRange');
```
Entrada
```json
 {
    "tenantid": "138",
    "record_start": "0",
    "page_length": "20",
    "filters": {
        "actives": "",
        "textsearch": ""
    },
    "order": "fullname"
}
```
Salida
```json
{
	"status": "ok",
	"message": {
		"total_records": 20,
		"data": [
			{
				"userid": "1992",
				"tenantid": "138",
				"fullname": "admin 2 test 1",
				"email": "admin2test@callevo.com",
				"usertype": "1",
				"description": "System Administrator",
				"phone_number": "",
				"teams": [
					"jjsc_tenant_test_team"
				],
				"created_at": "2023-04-20 14:02:14",
				"deleted_at": null
			},
			
		]
	}
}
```


```php
$app->post('/nocalled_range[/p/{p}/f/{f}/o/{o}/i/{i}]', \App\Controllers\LeadController::class . ':getNoCalledRange');
```
entrada
```
 {
	"cr":1,
	"m":"pooldisp",
	"poolid":969,
	"dispid":632,
	"attempt":1,
	"tenantid": 139,
	"record_start": 0,
	"filters": {
		
	}
}
```
salida
```
{
	"status": "ok",
	"message": {
		"total_records": 6,
		"record_start": 4,
		"page": "2",
		"total_pages": 2,
		"page_length": "3",
		"data": [
			{
				"lead_phone": "3174061995",
				"lead_fname": "Keith",
				"lead_lname": "Ragsdale",
				"lead_id": "5791877",
				"lastupdate": "2024-04-06 01:24:04",
				"prefix": "317",
				"state": "IN",
				"reccalled": "1",
				"nexttry": "0"
			},
			
		]
	}
}
```

$app->post('/leads_range', \App\Controllers\LeadController::class . ':getLeadsRange');
entrada
 {
    "tenantid": "98",
    "record_start": "0",
    "page_length": "20",
    "filters": {
        "where": "lead_fname like '%jorg%'"
    }
}
salida
{
	"status": "ok",
	"message": {
		"total_records": 54,
		"data": [
			{
				"lead_id": "694",
				"lead_fname": "Jorge",
				"lead_mname": "",
				"lead_lname": "Sainz",
				"lead_phone": "7209999999",
				"lead_email": "jjsc@domain.com",
				"lead_address": "Quito",
				"lastupdate": "2022-09-27 11:15:40",
				"lastcallresult": "0",
				"trynumbers": "0",
				"lead_company": "John The Riper C
				
			}
		]
	}
}

$app->post('/numbers_range[/p/{p}/f/{f}/o/{o}/i/{i}]', \App\Controllers\PhoneController::class . ':numbers');
entrada
{
  "fields": "phones.phoneid,phones.phone,phone_type.typename,phones.description,calleridgroup.group_name,prefix.prefix,phones.active,phones.flagged,phones.ratecenter",
  "order": "phones.phone",
  "where": ""
}
salida
{
	"status": "ok",
	"message": {
		"total_records": "43",
		"record_start": 1,
		"page": "1",
		"total_pages": 9,
		"page_length": "5",
		"data": [
			{
				"phoneid": "2546",
				"phone": "2053580111",
				"typename": "VIRTUAL",
				"description": "autumn_air",
				"group_name": "autumn_air",
				"prefix": "205",
				"active": "1",
				"flagged": "0",
				"ratecenter": ""
			},
			
		]
	}
}


# VAN Support 

Usa el tenantid para tomar los datos iniciales y construir el request dentro de cada ruta
```php
$app->post('/van', \App\Controllers\VANController::class . ':van');
```
entrada
```json
{
	"method": "GET",
	"url" : "https://api.securevan.com/v4",
	"apiToken": "d3ba3e06-9c36-b1b4-4798-bbc7afa6843c",
	"appName": "savedLists",
	"dbType": "1",
	"payload": {}
	
}
```
salida 
lo que venga de van
```php
$app->post('/importer_van', \App\Controllers\VANController::class . ':importer');
```
entrada
```json
{
  "method":"GET",
  "appName":"savedLists/568890",
  "tenantid":"97",
  "dbType":"0",
  "confPool":
     {
		 "camp_id":"385",
		 "allow_duplicate":"f",
		 "randomize":"y",
		 "CleanOld":"0",
		 "markFinalCRC":"0",
		 "prefixlen":"3",
		 "savedListId":"568890"
	}
}
```
salida
lo que venga de van

cuenta los pools cuyo field savedList corresponde al especificado

`ADMIN => ` En `Importer` obtiene la lista por ID

```php
$app->get('/van_list_id/{listid}', \App\Controllers\VANController::class . ':getVanListId');
```
salida 
1

Toma de VAN las preguntas para guardarlas en la base
```php
$app->post('/sync_van_questions', \App\Controllers\VANController::class . ':syncQuestions');
```
salida
```json
{
	"status": "ok",
	"message": "Done total: 53, inserted: 0 records"
}
```

Toma los disposition de VAN para guardarlos en la base
```php
$app->post('/sync_van_dispositions', \App\Controllers\VANController::class . ':syncResultCodes');
```
salida
```
{
	"status": "ok",
	"message": "Done total: 8, inserted: 8 records"
}
```
Toma los activists de VAN y los guarda en la base
```php
$app->post('/sync_van_leadflag', \App\Controllers\VANController::class . ':syncVanActivists');
```
salida
```json
{
	"status": "ok",
	"message": "Done total:54,  inserted:0 records"
}
```
Actualiza en el tenant el api que se especifica
$app->put('/van_data/{tenantid}', \App\Controllers\VANController::class . ':vanApiData');
entrada
{
	"ngp_van_apikey" ""ertewrtertetwetwerterw"
}
salida
{
	"status" : "ok", 
	"message" : "successfull"
}

$app->get('/van_api_key_test[/{apiKey}]', \App\Controllers\VANController::class . ':testVanApiKey');
salida
lo que venga de van


/**
* ==========================  WEBFORM ===========================================
*/
Agrega/modifica un webform
$app->post('/webform', \App\Controllers\WebFormController::class . ':modifyWebForm');
$app->put('/webform', \App\Controllers\WebFormController::class . ':modifyWebForm');
{
	"webform_id" : -1, 
	"description": "",
	"url": "",
	"method": "",
	"camp_id": "",
	"tenantid": "",
	"fields" : [
		{
			"label_field": "",
			"field_webform": "",
			"field_lead": "",
		},
		
	]
}

Borra un webform
$app->delete('/webform/{id}', \App\Controllers\WebFormController::class . ':deleteWebForm');

$app->post('/webform/active/{id}/{action}', \App\Controllers\WebFormController::class . ':activeWebForm');

```
```
```
```



`ADMIN =>` Obtiene un nombre unico para crear usuario `u` o teams `q`.

```php
$app->get('/uniquename', \App\Controllers\UserController::class . ':getUserNameUnique');
```
parametros de entrada
```js
let data = { 
	"tenantID": "{{auth.user.tenantid}}",
	"prefix": "u"
};
```
respuesta
```json
{"generated":"e76ea3aa25f01f96ecbe"}
```

