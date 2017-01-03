Mashape APIs

# aqi
curl --get --include 'https://simple-weather.p.mashape.com/aqi?lat=1.0&lng=1.0' \
  -H 'X-Mashape-Key: pbhQPUuLM4msh8OLRZBJBEQYDqS5p1DgNvrjsnNQrzzbs2G4an' \
  -H 'Accept: text/plain'

# weather
curl --get --include 'https://simple-weather.p.mashape.com/weather?lat=1.0&lng=1.0' \
  -H 'X-Mashape-Key: pbhQPUuLM4msh8OLRZBJBEQYDqS5p1DgNvrjsnNQrzzbs2G4an' \
  -H 'Accept: text/plain'

# weatherdata
curl --get --include 'https://simple-weather.p.mashape.com/weatherdata?lat=1.0&lng=1.0' \
  -H 'X-Mashape-Key: pbhQPUuLM4msh8OLRZBJBEQYDqS5p1DgNvrjsnNQrzzbs2G4an' \
  -H 'Accept: application/json'
