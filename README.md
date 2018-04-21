# Profile

> "Think RSS meets twitter"

Profile is a self-hosted micro-blogging network for individuals who own their data.

Put simply, a Profile is a JSON file that is hosted on a web server. Each file represents the profile of an individual. From their profile, an individual can reveal as much or as little as they wish about themselves. They can also attach links to pictures, write simple text posts, update their bio and list their hobbies and fellow profile friends.

Profilers interact through a browser extension. From the extension, Profilers are able to subscribe to other Profilers to receive updates.

The core of the standard is designed to be as small and minimal as possible. This allows for interactive features and services to be built on top of the protocol making the Profile social platform extensive and fun to play with.

## How can I get started?
The easiest way to get started is by creating your very own profile right [here](https://github.com/chickencoder/profile-starter)

## Creating a Profile
Creating a profile is as simple as writing a text file. Using a text editor such as VS Code, Atom etc. simple create a new file called `profile.json`. The file must be correctly formatted in JSON, so if you're unfamiliar then you should [read about it](https://www.w3schools.com/js/js_json_syntax.asp) first.

## Required Fields
The following fields **must** be included within your Profile JSON file to be a valid Profile.

#### Meta
The `meta` field must be an object containing two other mandatory fields: `url` and `version`. The `url` field must be a string formatted as a URL pointing to this json file. The `version` field must be a string representing the Profile version. This field can be left blank which will signify the very latest version of the standard. For example...

```json
{
    "meta": {
        "url": "https://somewebsite.com/profile.json",
        "version": "*"
    }
}
```

#### Name
The `name` field must be a string containing your full name or any name you wish to use for your Profile. This field must not be blank. For example...

```json
{
    "name": "Joe Bloggs"
}
```

#### Bio
The `bio` field must be a string that is no longer than 256 characters containing a brief summary of who you are. For example...

```json
{
    "bio": "I am just a silly example. I don't exist"
}
```

#### Interests
The `interests` field must be an array of strings each labelling an interest of yours. For example...

```json
{
    "interests": ["coffee", "cycling", "reading"]
}
```

#### Posts
The `posts` field must be an array of objects. Each object should following the post structure outlined [below](#post). The post array can be empty. 

## Optional Fields
Profilers are encouraged to use the following fields to make the most out of their Profile, however, they are not required.

#### Nickname
The `nickname` field must be a string representing an informal nickname that the Profiler wishes to be shown on their profile.

```json
{
    "nickname": "007"
}
```

#### Picture
The `picture` field must be a string representing a URL that points to an image file. This file should represent your profile. For example, it could be a picture of yourself or a symbol...

```json
{
    "picture": "https://somewebsite.com/someimage.jpg" 
}
```

#### Friends
The `friends` field must be an object. The key of each field within the object should be a name and the value of each key should be a URL to that Profiler's profile. For example...

```json
{
    "friends": {
        "alice": "https://alice.awebsite.org/profile.json",
        "bob": "https://bob.somewebsite.com/profile.json"
    }
}
```

#### Links
The `links` field must be an object. The key of each field within the object should be a title given to a link and the value of each key should a URL that points to any web link. For example...

```json
{
    "links": {
        "My Github": "https://github.com/chickencoder",
        "My Twiter": "https://github.com/jessethesibley"
    }
}
```
#### Following
The `following` field must be an array containing URLs pointing to other `profile.json` files. All valid profiles listed in this array will be shown on your feed.

```json
{
    "following": ["https://winegum.netlify.com/profile.json"]
}

<h2 name="post">A Post</h2>
A post is an object that should be used within the `posts` field array. Each object must contain a `content` field and `timestamp` field. Optionally a post can contain an `link` field, and a `tags` field. The `content` field must be a string that is 256 characters or less, the `timestamp` field must be a number formatted as a UNIX timestamp representing the time of the post, the `link` field must be a string containing URL relating to the content of the post and the `tags` field must be an array containing strings of categories the post could be related to. For example...

```json
{
    "posts": [
        {
            "content": "Hello World! This is my first post",
            "timestamp": 0,
            "link": "https://en.wikipedia.org/wiki/%22Hello,_World!%22_program",
            "tags": ["Hello", "World"]
        }
    ]
}
```

## Contributing
If you'd like to contribute ideas to the standard, design work or just become a community member, tweet me @JesseTheSibley or leave an issue and maybe we'll start a Slack.