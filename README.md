# Specter Edge

## Executive summary

Specter Edge lets an operator run field tasks on remote devices from a chat window. You type a command in the <img src="https://icon.icepanel.io/AWS/svg/Business-Applications/Wickr.svg" width="16" alt=""> [AWS Wickr](https://aws.amazon.com/wickr/) app on a phone or laptop, a message travels through <img src="https://icon.icepanel.io/AWS/svg/Internet-of-Things/IoT-Core.svg" width="16" alt=""> [AWS IoT Core](https://aws.amazon.com/iot-core/) to a <img src="https://cdn.simpleicons.org/raspberrypi" width="16" alt=""> [Raspberry Pi](https://www.raspberrypi.com) in the field, the Pi runs the matching task inside a container, and the result comes back to the same chat. Two devices share the one command plane: a signals device that hears radio, and a rover that sees with a camera. Every radio task is receive-only: the radio never transmits.

- **Chat control.** The operator types a command in <img src="https://icon.icepanel.io/AWS/svg/Business-Applications/Wickr.svg" width="16" alt=""> [AWS Wickr](https://aws.amazon.com/wickr/) on a phone or laptop and gets the answer in the same conversation. A Wickr bot hands each command to a <img src="https://icon.icepanel.io/AWS/svg/Compute/Lambda.svg" width="16" alt=""> [AWS Lambda](https://aws.amazon.com/lambda/) command menu, which publishes it on an <img src="https://icon.icepanel.io/AWS/svg/Internet-of-Things/IoT-Core.svg" width="16" alt=""> [AWS IoT Core](https://aws.amazon.com/iot-core/) topic; results return the same way.
- **Signals device.** A <img src="https://cdn.simpleicons.org/raspberrypi" width="16" alt=""> [Raspberry Pi](https://www.raspberrypi.com) runs <img src="https://icon.icepanel.io/AWS/svg/Internet-of-Things/IoT-Greengrass.svg" width="16" alt=""> [AWS IoT Greengrass](https://aws.amazon.com/greengrass/) and a <img src="https://cdn.simpleicons.org/kalilinux" width="16" alt=""> [Kali Linux](https://www.kali.org) container that drives a HackRF software-defined radio. One radio, many bands: the HackRF hears Bluetooth, Wi-Fi, GPS and Sub-GHz, and every one is receive-only.
- **Rover.** A second <img src="https://cdn.simpleicons.org/raspberrypi" width="16" alt=""> [Raspberry Pi](https://www.raspberrypi.com) carries a camera turret and a small container that runs computer-vision detection, then reports what it finds back over the same path.
- **Artifacts.** Device packages are stored in <img src="https://icon.icepanel.io/AWS/svg/Storage/Simple-Storage-Service.svg" width="16" alt=""> [Amazon S3](https://aws.amazon.com/s3/).
- **Deploy.** <img src="https://cdn.simpleicons.org/terraform" width="16" alt=""> [Terraform](https://www.terraform.io) declares every resource, from the artifact bucket and the device components to the rollout, and one <img src="https://cdn.simpleicons.org/githubactions" width="16" alt=""> [GitHub Actions](https://docs.github.com/actions) workflow applies it.

## In action

A recording is not made yet. It will be added once the chat command path is finished.

## Architecture

An operator command in a chat app reaches two Raspberry Pi edge devices: a signals device that hears radio through plug-in modules, and a rover that sees with a camera turret. Results return the same way.

![Specter Edge architecture: Wickr command, Lambda command menu, IoT Core topic, Greengrass on two Raspberry Pis, a signals device with receive-only radio abilities and a rover with computer vision](assets/specter-edge.png)

## License

PolyForm Noncommercial 1.0.0 with a required notice from Haya Tech LLC. Noncommercial use is free; any commercial use, including resale, hosting for others, or a paid product, needs a written license from Haya Tech LLC first. See [LICENSE](LICENSE).
