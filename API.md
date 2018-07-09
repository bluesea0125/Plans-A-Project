### Questions
    1. JSON or PACKET
    2. Is it possible that JSON Format is used for real time data streaming?
    3. Most of CV APIs support JSON Interface. Do they support real time also?
      ->Azure says possible.
       https://azure.microsoft.com/en-us/services/cognitive-services/computer-vision/
       
### API
    {[
        {
            "cameraid" : 0,
            "frameid" : 20131212411,
            "entities" : [
                          {
                            "class" : "vehicle",
                            "type" : "truck"
                            "license" : "粤B12345",
                            "position" : [10,20,100,200]#[x,y,width,height]
                          },
                          
                         ]
         },
         {
         },
      ]}    
### Layer-1
    Object Detection
    { [{
          "class": "vehicle"
          "position": {
                            "left": 100,
                            "top": 100,
                            "width": 200,
                            "height": 300
                        }
        },
        {
          "class": "ped"
          "position": {
                            "left": 300,
                            "top": 100,
                            "width": 30,
                            "height": 80
                        }                    
    }
    
    
### Layer-2


