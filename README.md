# gm_formdata
Simple library to generate a multipart/form-data body

## Usage
```lua
require( "formdata" )

local form = FormData()
form:Append( "payload_json", { content = "Hello!" } )
form:Append( "files[0]", fileData, "image.png" )

-- This is just a usage example, you can't actually send Webhooks like this
-- (Discord blocks GMod's base HTTP requests)
HTTP( {
    method = "POST",
    url = "https://discord.com/api/webhooks/blah/blah",
    headers = {
        ["Content-Type"] = table.Add(
            form:GetHeaders(),
            { ["User-Agent"] = "GmodIntegration v1.0" }
        )
    },
    body = form:Read(),
    success = function() end,
    failed = function() end
})
```
