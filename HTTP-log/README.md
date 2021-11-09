curl --location -g --request POST 'http://192.168.63.100:5000/v3/auth/tokens' \
--header 'Content-Type: application/json' \
--data-raw '{
	"auth": {
		"identity": {
			"methods": ["password"],
			"password": {
				"user": {
					"domain": {
						"name": "default"
					},
					"name": "admin",
					"password": "cone@234"
				}
			}
		},
		"scope": {
			"project": {
				"domain": {
					"name": "default"
				},
				"name": "admin"
			}
		}
	}
}'

curl -i $PROXY_IP/http_osp/sample --data-raw '{
"auth": {
"identity": {
"methods": ["password"],
"password": {
"user": {
"domain": {
"name": "default"
},
"name": "admin",
"password": "cone@234"
}
}
},
"scope": {
"project": {
"domain": {
"name": "default"
},
"name": "admin"
}
}
}
}