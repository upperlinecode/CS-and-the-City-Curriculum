# Excerpt

## When It Comes to Gorillas, Google Photos Remains Blind (in [Wired](https://www.wired.com/story/when-it-comes-to-gorillas-google-photos-remains-blind/))

In 2015, A black software developer embarrassed Google by tweeting that the company’s Photos service had labeled photos of him with a black friend as “gorillas.” Google declared itself “appalled and genuinely sorry.” An engineer who became the public face of the clean-up operation said the label gorilla would no longer be applied to groups of images, and that Google was “working on longer-term fixes.”

More than two years later, one of those fixes is erasing gorillas, and some other primates, from the service’s lexicon. The awkward workaround illustrates the difficulties Google and other tech companies face in advancing image-recognition technology, which the companies hope to use in self-driving cars, personal assistants, and other products.

WIRED tested Google Photos using a collection of 40,000 images well-stocked with animals. It performed impressively at finding many creatures, including pandas and poodles. But the service reported “no results” for the search terms “gorilla,” “chimp,” “chimpanzee,” and “monkey.”

Google Photos, offered as a mobile app and website, provides 500 million users a place to manage and back up their personal snaps. It uses machine-learning technology to automatically group photos with similar content, say lakes or lattes. The same technology allows users to search their personal collections.

In WIRED’s tests, Google Photos did identify some primates. Searches for “baboon,” “gibbon,” “marmoset,” and “orangutan” functioned well. Capuchin and colobus monkeys could be found as long as a search used those terms without appending the M-word.

In another test, WIRED uploaded 20 photos of chimps and gorillas sourced from nonprofits Chimp Haven and the Dian Fossey Institute. Some of the apes could be found using the search terms “forest,” “jungle,” or “zoo,” but the remainder proved difficult to surface.

The upshot: Inside Google Photos, a baboon is a baboon, but a monkey is not a monkey. Gorillas and chimpanzees are invisible.

In a third test attempting to assess Google Photos’ view of people, WIRED also uploaded a collection of more than 10,000 images used in facial-recognition research. The search term “African american” turned up only an image of grazing antelope. Typing “black man,” “black woman,” or “black person,” caused Google’s system to return black-and-white images of people, correctly sorted by gender, but not filtered by race. The only search terms with results that appeared to select for people with darker skin tones were “afro” and “African,” although results were mixed.

A Google spokesperson confirmed that “gorilla” was censored from searches and image tags after the 2015 incident, and that “chimp,” “chimpanzee,” and “monkey” are also blocked today. “Image labeling technology is still early and unfortunately it’s nowhere near perfect,” the spokesperson wrote in an email, highlighting a feature of Google Photos that allows users to report mistakes.

Google’s caution around images of gorillas illustrates a shortcoming of existing machine-learning technology. With enough data and computing power, software can be trained to categorize images or transcribe speech to a high level of accuracy. But it can’t easily go beyond the experience of that training. And even the very best algorithms lack the ability to use common sense, or abstract concepts, to refine their interpretation of the world as humans do.

As a result, machine-learning engineers deploying their creations in the real world must worry about “corner cases” not found in their training data. “It’s very hard to model everything your system is going to see once it’s live,” says Vicente Ordóñez Román, a professor at the University of Virginia. He contributed to research last year that showed machine-learning algorithms applied to images could pick up and amplify biased views of gender roles.

Google Photos users upload photos snapped under all kinds of imperfect conditions. Given the number of images in the massive database, a tiny chance of mistaking one type of great ape for another can become a near certainty.

Google parent Alphabet and the wider tech industry face versions of this problem with even higher stakes, such as with self-driving cars. Together with colleague Baishakhi Ray, an expert in software reliability, Román is probing ways to constrain the possible behaviors of vision systems used in scenarios like self-driving cars. Ray says there has been progress, but it is still unclear how well the limitations of such systems can be managed. “We still don’t know in a very concrete way what these machine learning models are learning,” she says.

Some of Google’s machine-learning systems are permitted to detect gorillas in public. The company’s cloud-computing division offers businesses a service called Cloud Vision API to build into their own projects. When WIRED tested the online demo with gorilla and chimp photos, it identified both.

One photo of an adult gorilla cradling baby twins was tagged by Google’s Cloud Vision service as “western gorilla” with a confidence rating of 94 percent, for example. The system returns a list of its best guesses at relevant tags for an image. “Mammal,” and “primate” also scored 90 percent or more.