### Questions
    1. JSON or PACKET
    2. Is it possible that JSON Format is used for real time data streaming?
    3. Most of CV APIs support JSON Interface. Do they support real time also?
      ->Azure says possible.
       https://azure.microsoft.com/en-us/services/cognitive-services/computer-vision/
      ->Experiment prove it
       https://github.com/bluesea0125/tests-http-streaming
       
### Architecture
    - IN
    DataStream-->Processing Server-->Result-->|
                                              |-->SQL Server-->|
                                                               |--->DB
    - OUT
    Request--------------------------------------------------->|
                                                               |<---DB   
                                              |<--SQL Server<--|
    Response<-----Web Server<------Result<----|

    
### SQL
    camera0=
                CREATE TABLE IF NOT EXISTS t_objdet_camera0_his (
                  `camera_id` tinyint(2) NOT NULL COMMENT 'CAMERA ID',
                  `frame_id` bigint(30) NOT NULL COMMENT 'FRAME INDEX',
                  `object_id` smallint(3) NOT NULL COMMENT 'OBJECT INDEX',
                  `object_class` tinyint(2) NOT NULL COMMENT '0:VEHICLE,1:PEDESTRIAN,2:MOTORCYCLE',
                  `object_type` varchar(20) DEFAULT NULL COMMENT 'TYPE',
                  `object_colr` varchar(20) DEFAULT NULL COMMENT 'COLOR',
                  `vehicle_license` varchar(20) DEFAULT NULL COMMENT 'VEHICLE LICENSE',
                  `person_name` varchar(20) DEFAULT NULL COMMENT 'HUMAN NAME',
                  `person_gender` tinyint(2) DEFAULT NULL COMMENT '0:MALE,1:FEMALE',
                  `person_age` smallint(3) DEFAULT NULL COMMENT 'HUMAN AGE',
                  `left` smallint(4) NOT NULL COMMENT 'POSITION LEFT',
                  `top` smallint(4) NOT NULL COMMENT 'POSITION TOP',
                  `width` smallint(4) NOT NULL COMMENT 'POSITION WIDTH',
                  `height` smallint(4) NOT NULL COMMENT 'POSITION HEIGHT',
                  `create_time` bigint(20) NOT NULL COMMENT 'CREATE TIME',
                  `status` tinyint(2) DEFAULT NULL COMMENT '0:NORMAL,1:OVERSTAY,2:INVERSE,3:INVERSE'
                ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
                
# APIs
### [General]
    Request: http://127.0.0.1:9000/0/objdet
    Response:
    {
        'camera_id':0, # CAMERA ID
        'frame_id':192010020, # FRAME INDEX
        'objects': [{  
                    'object_id':, # VEHICLE LICENSE OR HUMAN NAME
                    'object_class': ,# 0:VEHICLE, 1:PEDESTRIAN, 2:MOTORCYCLE
                    'object_subclass':  ,# TYPE
                    'object_colr': ,# COLOR
                    'position':{'left': ,# LEFT
                                'top': ,# TOP
                                'width': ,# WIDTH
                                'height': ,# HEIGHT},# POSITION
                    status:0 # 0:NORMAL,1:OVERSTAY, 2:INVERSE, 3:INVERSE},
                    {
                    'object_id':, # VEHICLE LICENSE OR HUMAN NAME
                    'object_class': ,# 0:VEHICLE, 1:PEDESTRIAN, 2:MOTORCYCLE
                    'object_subclass':  ,# 0:CHILD, 1:ADULT
                    'object_colr': ,# COLOR
                    'person_gender': ,# 0:MALE,1:FEMALE
                    'person_age': ,# HUMAN AGE
                    'position':{'left': ,# LEFT
                                'top': ,# TOP
                                'width': ,# WIDTH
                                'height': ,# HEIGHT},# POSITION
                    status:0 # 0:NORMAL,1:OVERSTAY, 2:INVERSE, 3:INVERSE}
                    ]
      }
### []
