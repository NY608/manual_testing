# manual_testing
#script for finding Response time of https://bstackdemo.com/signin using powershell.
$uri = "https://bstackdemo.com/signin"
$request = Measure-Command {
    $response = Invoke-WebRequest -Uri $uri
}
"Time to Connect: $(($response.RawContentLength / 1KB).ToString('N2')) KB"
"Time to First Byte: $($response.Headers.'Date')"
"Total Time: $($request.TotalMilliseconds) ms"



