# gm_formdata
Simple library to generate a multipart/form-data body

## Usage
```lua
require( "formdata" )

local form = FormData()
form:Append( "payload_json", { content = "Hello!" } )
form:Append( "files[0]", fileData, "image.png" )

-- This won't actually work, Discord rejects our messages from GMod's HTTP lib
HTTP( {
    method = "POST",
    url = "https://discord.com/api/webhooks/blah/blah",
    headers = {
        ["Content-Type"] = table.Add(
            form:GetHeaders(),
            { ["User-Agent"] = "GmodIntegration v1.0" }
        )
    },
    success = function() end,
    failed = function() end
})
```
