{
  "name": "Automation 1",
  "nodes": [
    {
      "parameters": {
        "content": "# Automation 1\n\n### First automation t understand the working of nodes and insight seings or configuration\n\n\n",
        "width": 272
      },
      "type": "n8n-nodes-base.stickyNote",
      "position": [
        -400,
        -112
      ],
      "typeVersion": 1,
      "id": "824b1857-6d33-43db-a09b-30b92564eeb0",
      "name": "Sticky Note"
    },
    {
      "parameters": {
        "formTitle": "Mohammad Consultation Form",
        "formDescription": "Hi there, glad to meet you.\nPlease fill in he bellow details so as to connect with mohammad for ai consultation or training",
        "formFields": {
          "values": [
            {
              "fieldLabel": "Name",
              "placeholder": "Your Name"
            },
            {
              "fieldLabel": "Service",
              "fieldType": "dropdown",
              "fieldOptions": {
                "values": [
                  {
                    "option": "Consultation"
                  },
                  {
                    "option": "Training"
                  }
                ]
              }
            }
          ]
        },
        "options": {
          "appendAttribution": true,
          "buttonLabel": "Let Aify your world"
        }
      },
      "type": "n8n-nodes-base.formTrigger",
      "typeVersion": 2.5,
      "position": [
        -384,
        112
      ],
      "id": "acdba2d2-28fe-44e4-947e-14583409c1e5",
      "name": "On form submission",
      "webhookId": "4f988276-5920-4233-b27c-6b2f4c9b597b",
      "notesInFlow": true,
      "notes": "My first Form"
    },
    {
      "parameters": {
        "operation": "append",
        "documentId": {
          "__rl": true,
          "value": "1NVUQJ-sG7TThcAe3GNZILOnjWK3lYr7Pa331PxS054g",
          "mode": "list",
          "cachedResultName": "leads",
          "cachedResultUrl": "https://docs.google.com/spreadsheets/d/1NVUQJ-sG7TThcAe3GNZILOnjWK3lYr7Pa331PxS054g/edit?usp=drivesdk"
        },
        "sheetName": {
          "__rl": true,
          "value": "gid=0",
          "mode": "list",
          "cachedResultName": "Sheet1",
          "cachedResultUrl": "https://docs.google.com/spreadsheets/d/1NVUQJ-sG7TThcAe3GNZILOnjWK3lYr7Pa331PxS054g/edit#gid=0"
        },
        "columns": {
          "mappingMode": "defineBelow",
          "value": {
            "name": "={{ $json.Name }}",
            "service": "={{ $json.Service }}",
            "time": "={{ $json.submittedAt }}"
          },
          "matchingColumns": [],
          "schema": [
            {
              "id": "name",
              "displayName": "name",
              "required": false,
              "defaultMatch": false,
              "display": true,
              "type": "string",
              "canBeUsedToMatch": true
            },
            {
              "id": "service",
              "displayName": "service",
              "required": false,
              "defaultMatch": false,
              "display": true,
              "type": "string",
              "canBeUsedToMatch": true
            },
            {
              "id": "time",
              "displayName": "time",
              "required": false,
              "defaultMatch": false,
              "display": true,
              "type": "string",
              "canBeUsedToMatch": true
            }
          ],
          "attemptToConvertTypes": false,
          "convertFieldsToString": false
        },
        "options": {}
      },
      "type": "n8n-nodes-base.googleSheets",
      "typeVersion": 4.7,
      "position": [
        -176,
        112
      ],
      "id": "71a8b0a1-a31e-43c6-9ec6-1ac2628efcf2",
      "name": "Append row in sheet",
      "credentials": {
        "googleSheetsOAuth2Api": {
          "id": "wory9RGTkX5QemrS",
          "name": "Google Sheets account 3"
        }
      },
      "notes": "my first sheet"
    },
    {
      "parameters": {
        "sendTo": "mohammad70623@gmail.com",
        "subject": "form leads update",
        "emailType": "text",
        "message": "=hi mohammad\nhow ae you?\nthere is new leads on the form.\nName:  {{ $json.name }}\nService: {{ $json.service }}\nTime : {{ $json.time }}\n\nSource: {{ $workflow.id }}\n\nThanks\nyour awsome workflow ",
        "options": {
          "appendAttribution": true
        }
      },
      "type": "n8n-nodes-base.gmail",
      "typeVersion": 2.2,
      "position": [
        32,
        112
      ],
      "id": "425a9fda-eec3-470c-95ba-2a416a280f79",
      "name": "Send a message",
      "webhookId": "96054f67-7e0c-45a7-9743-3c856254b5e6",
      "credentials": {
        "gmailOAuth2": {
          "id": "ZjRniltAWsm5oYjn",
          "name": "Gmail account 2"
        }
      }
    }
  ],
  "pinData": {},
  "connections": {
    "On form submission": {
      "main": [
        [
          {
            "node": "Append row in sheet",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "Append row in sheet": {
      "main": [
        [
          {
            "node": "Send a message",
            "type": "main",
            "index": 0
          }
        ]
      ]
    }
  },
  "active": false,
  "settings": {
    "executionOrder": "v1",
    "binaryMode": "separate",
    "availableInMCP": false
  },
  "versionId": "b85b93e1-39ae-42e7-b9b6-7376cfea8de0",
  "meta": {
    "templateCredsSetupCompleted": true,
    "instanceId": "bf772102aaa24de2edf2faee9002f63e4a6efcf8262bbf982841a70931d12aaf"
  },
  "id": "LeUX1p7G3lLQBvgF",
  "tags": []
}
