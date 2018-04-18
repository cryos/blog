+++
description = "JSON key naming - should we use camelCase, kebab-case or snake_case?"
categories = ["programming"]
tags = ["open-science", "json"]
images = [""]
banner = ""
date = "2018-04-18T08:45:00-04:00"
title = "JSON: Camels, Kebabs and Snakes"
menu = ""

+++

I do a lot of work using [JSON][json] (JavaScript Object Notation), and last week I ran my first ever poll on Twitter posing the question of which naming convention people prefer for keys. A quick survey of its use in the wild reveals common use of [camelCase][camelCase], [kebab-case][kebab-case], and [snake_case][snake_case]. These are all things I was aware of, but I only knew the name for the first one until a year or so ago. There are Wikipedia articles dedicated to two of the three of them!

<!--more-->

{{< tweet 984196036863262720 >}}

I have had some discussion about this at a few meetings/workshops, and have had a role in defining some RESTful APIs and JSON data container specifications. I was a little surprised by the extremely unscientific poll that garnered 22 votes (interestingly it will not let you vote on your own poll). I worry for the people voting for a mixture of the above, and hope they were just trying to wind me up :-)

### Languages Using JSON

I had thought that camel case would have been the most popular as it is the preferred convention in JavaScript, but it is clear that JSON is much larger than just JavaScript. There is actually a really nice set of answers on stackoverflow, [JSON naming convention][stackoverflow-json], that confirms there is no single standard.

I don't know how to link to a specific answer, but the third answer with the title "Premise" has a good discussion. It basically follows the logic that you consider the languages being used to generate or parse the JSON. It makes the case that Python and PHP favor snake case, whereas Java and JavaScript favor camel case. It also looks at a number of implementations, such as Google Maps (camel case), Facebook (snake case), Amazon Web Services (snake and camel?!?), and [JSON-LD][json-ld] (camel case and proper camel case).

### What Shoud You Use?

I have apparently been following the premise of that post for quite some time, C++ (at least the conventions I am used to using) favors camel cased (STL favors snakes), as does JavaScript. I do more and more in Python these days, but snake case doesn't come as naturally to me. I would also like to build bridges from some of the work we are doing to JSON-LD, which points to the use of camel case making this a little easier.

At the end of the day it doesn't matter too much so long as you are consistent, and don't use spaces as that can cause all sorts of headaches. I need to go and fix some things I did where we used spaces...

[json]: https://www.json.org/
[camelCase]: https://en.wikipedia.org/wiki/Camel_case
[kebab-case]: https://en.wikipedia.org/wiki/Letter_case#Special_case_styles
[snake_case]: https://en.wikipedia.org/wiki/Snake_case
[stackoverflow-json]: https://stackoverflow.com/questions/5543490/json-naming-convention
[json-ld]: https://json-ld.org/
