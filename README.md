# Reptile Monitoring System

## About
This is the hardware portion of a proof-of-concept system for monitoring reptile enclosures. This monitoring system is my senior project submission for Cal Poly, and was completed during the 2020-2021 academic year. The project was advised by Dr. Theresa Migler and is in partial fulfillment of the requirements for the degree of B.S. 

The repository for the related AWS backend of the project can be found [here](). The accompanying mobile application's repository can be found [here]()

## Details
The monitoring system is broken into two primary functions: capturing sensor data, and forwarding video footage. 

### Structure

* `src/monitoring.py` - The script that captures humidity and temperature data, and reports them to an IoT Core topic.
* `src/amazon-kinesis-video-streams-producer-sdk-cpp` - The sample repository from Amazon for streaming video to an AWS Kinesis Video stream.
* `src/camera_test.py` - A script no longer used. Was a proof-of-concept for detecting motion within an enclosure.
* `certs/` - The directory which should house any sensitive/secret files for the project. 
* `start.sh` - A script that should simplify the process for beginning the monitoring process.


## Getting Started

In order to meaningfully use this repository, you will need to recreate some portion of the AWS cloud backend. Instruction for which can be found [here]().

### Prerequisites

You have the following equipment:
* 1x Raspberry Pi 3B 
* 1x DHT22 Humidity and Temperature sensor
* 1x Raspberry Pi Camera module

Have already configured SSH on the Raspberry Pi, and ensure that Python 3 and gcc are installed and present on the device.

Have an IoT Core Rule configured, and an Amazon Kinesis Video stream enabled under the name "enclosure".

### Setup
0. SSH onto the Raspberry PI
1. Clone the repository
2. Add the submodule for the kinesis-video-streams-producer project. Under `/src/amazon-kinesis-video-streams-producers-sdk-cpp`
3. Build the submodule according to its README
4. Generate the secret files from the IoT Core service and the IAM role that's associated with it. 
5. Move these secret files to the `/certs/` folder.
6. Run the `./start.sh`. (You may need to run `chmod +x start.sh`, prior to running the script.)
