# Profile

Profile is a self-hosted, micro-blogging platform for individuals who own their data. Profile is a standard for defining `profile.yaml` files which are the building blocks of the Profile network.

## Getting started
The easiest way to get started is by creating your very own profile right [here](https://github.com/profile-project/profile-starter)!

## What is Profile
Put simply, a Profile is a YAML file that exists somewhere on the web. Each file represents the profile of an individual. From their profile, an individual can reveal as much or as little as they wish about themselves. They can also attach links to pictures, write simple text posts, update their bio and list their hobbies and fellow profile friends.

Consider your profile to be an RSS-like feed, owned, controlled by you that can be customised like an old-school geocities site and shared as publicly as a twitter feed.

The core of the standard is designed to be as small and minimal as possible. This allows for interactive features and services to be built on top of the protocol making the Profile social platform extensive and fun to play with.

The main idea behind Profile is to make the web fun again by utilising modern web technologies (such as the JAM stack) to create a decentralised platform.

[Check out an example](https://winegum.netlify.com/profile)

## Creating a Profile
Creating a profile is as simple as writing a text file. Using a text editor such as VS Code, Atom etc. simple create a new file called `profile.yaml`. Profile uses the YAML format to represent your data which you can learn more about [here](http://yaml.org/start.html)

## Required Fields
The following fields **must** be included within your Profile yaml file to be a valid Profile.

#### Meta
The `meta` field must be an object containing two other mandatory fields: `url` and `version`. The `url` field must be a string formatted as a URL pointing the root directory which contains your profile.yaml file. For example...

```yaml
meta:
    url: "https://youruser.somesite.com/"
```

#### Me
The `me` field contains the rest of the fields listed below. Each field, whether required or not, should be a sub-field of the `me` field.

#### Name
The `name` field must be a string containing your full name or any name you wish to use for your Profile. This field must not be blank. For example...

```yaml
name: "Joe Bloggs"
```
#### Bio
The `bio` field must be a string that is no longer than 256 characters containing a brief summary of who you are. For example...

```yaml
bio: >
I like to make fresh salads
and sunbathe.
```
#### Interests
The `interests` field must be an array of strings each labelling an interest of yours. For example...

```yaml
interests:
    - coffee
    - cycling
    - reading
```

#### Posts
The `posts` field must be an array of objects. Each object should following the post structure outlined [below](#post). The post array can be empty. 

## Optional Fields
Profilers are encouraged to use the following fields to make the most out of their Profile, however, they are not required.

#### Nickname
The `nickname` field must be a string representing an informal nickname that the Profiler wishes to be shown on their profile.

```yaml
nickname: "007"
```

#### Picture
The `picture` field must be a string representing a URL that points to an image file. This file should represent your profile. For example, it could be a picture of yourself or a symbol...

```yaml
picture: "https://somewebsite.com/someimage.jpg" 
```

#### Friends
The `friends` field must be an object. The key of each field within the object should be a name and the value of each key should be a URL to that Profiler's profile. For example...

```yaml
friends:
    - alice: "https://alice.awebsite.org/profile.yaml",
    - bob: "https://bob.somewebsite.com/profile.yaml"
```

#### Links
The `links` field must be an object. The key of each field within the object should be a title given to a link and the value of each key should a URL that points to any web link. For example...

```yaml
links:
    - Github: "https://github.com/chickencoder",
    - Twiter: "https://github.com/jessethesibley"
```
#### Following
The `following` field must be an array containing URLs pointing to other the root of other `profile.yaml` files. All valid profiles listed in this array will be shown on your feed.

```yaml
following: 
    - "https://winegum.netlify.com/"
```

<h2 name="post">Post</h2>
A post is an object that should be used within the `posts` field array. Each object must contain a `content` field and `timestamp` field. Optionally a post can contain an `link` field, and a `tags` field. The `content` field must be a string that is 256 characters or less, the `timestamp` field must be a number formatted as a UNIX timestamp representing the time of the post, the `link` field must be a string containing URL relating to the content of the post and the `tags` field must be an array containing strings of categories the post could be related to. For example...

```yaml
posts:
    - content: "Hello World! This is my first post"
      timestamp: 0
      link: "https://en.wikipedia.org/wiki/%22Hello,_World!%22_program"
      tags: 
        - "Hello"
        - "World"
```

## Example

```yaml
meta:
  url: 'https://winegum.netlify.com'

me:
  name: "Jesse Sibley"
  nickname: "Winegum" 
  picture: "/pictures/profile.jpg"
  bio: >
    I write code, drink coffee
    and dream data.

  interests:
    - "Cycling"
    - "Coffee"
    - "Culture"

  posts:
    - content: "Hello World!"
      timestamp: 123456789

    - content: "My Second Post"
      timestamp: 1234567890
      tags:
        - "Second"
        - "Post"
  friends:
    - alice: "https://alice.netlify.com"
    - bob: "https://bob.netlify.com"

```

## Project
The platform is currently being developed in many areas.
* [Profile App](https://github.com/profile-project/profile-app) Will be a web app for following other profiles and managing your own
* [Profile Post](https://github.com/profile-project/profile-post) Will be a validation network for submitting and validating posts on the platform
* [Profile Starter](https://github.com/profile-project/profile-starter) Is a kit for getting started with hosting your profile on Netlify
* [Profile Verify](https://github.com/profile-project/profile-verify) Will be a library for verifying profiles for use in profile-based applications.

## Contributing
If you'd like to contribute ideas to the standard, design work or just become a community member, tweet me [@JesseTheSibley](https://twitter.com/jessethesibley) or leave an issue and maybe we'll start a Slack.
