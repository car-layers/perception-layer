# Perception layer

The idea of this repo is to document a possible definition of what a perception layer of a vehicle could look like, this includes a data format that represents what a vehicle is "seeing" at a specific point in time as well as a stateful system that is able to keep track of then perceived entities over time and tell the user only the what has changed since last update.     

## Motivation

Vehicles can vary in many ways and each one can have a range of sensors that allows them to perceive the world in many diferent ways, data could come from cameras, radars, lidars, ultrasounds and the list keeps growing over time. For an agent trying to make use of this data it becomes problematic to adapt to such a diverse source of information when usually the information that matters is, what and where is around me. By having this information abstracted in a light weight format agents no longer care about the specific capabilities of a vehicle and doing expensive processing to extract relevant information.

## Format of single frame

We can't asume anything about the consumer of this data, it could be very resource constrained(e.g. a micro-controller) so we want our data format to be as light weight as possible but without going to far compromising developer friendliness and easy of use.  
My proposal here is to use a well known crossplatform binary serialization format, [protocol buffers](https://developers.google.com/protocol-buffers/) is one of the most popular choices in the market but I see the newer 0 copy alternatives as better choices, maybe not as popular as protobuf now but they will get there. I'm talking about [flatbuffers](https://google.github.io/flatbuffers/) and [Cap'n Proto](https://capnproto.org/), I have personal preference on the later but flatbuffers will probably become the most popular ... because google, I guess it would need some testing and bench marking.

A circular radar-like representation is a good way of showing whats-around-me kind of data since vehicles move in a plane, they are the center of the world and everything that comes into their range of vision pops up as a point in the radar. To represent the location of a point in a circle we need its angle and distance from the center, for some perceived entities a point might be enough but for some others we need a collection of points that form a shape or some boundries.  
As for what each point/group of points mean we also need to attach an identifier to distinguish objects based on categories and also differentiate different entities of the same kind.

```
// TODO
```

## Format of updates/diffs
TODO
