# Speech Patterns
When people train machines, they'll feed it millions of lines from movies, videos, etc, just so the AI has a variation in lines. Most of 
these lines are recorded in a Sequencing pattern, a lot being Sequence2Sequence. While this is a good way to give it variation, it 
doesn't actually teach the AI to speak. We always analyze the speech patterns of the input but never craft something based on those 
types of inputs it's received. So how can we get it to learn the structure of a sentence? To learn new defintions? What actually goes 
into our sentence structure patterns and determines how we speak? 

### Grammar
Obviously grammar is necessary for our speech patterns. We need to be able to teach it nouns, verbs, adjectives, etc. Thinking about it in 
relation to humans, we can get the AI to do it in a similar way. Parts of grammar aren't neceessarily repeated learning like we do with a 
lot of things. Our brain also works in a way where we try to piece things together in a patter, so why not let the AI do that as well? As 
we hear more sentences, our brain sees the pattern that sentences can take, no matter what language. We start off with simple words like 
"car" or "tree", learning that to notice something, we say "that's a car". So how do we get the AI to learn of the sentence structures?

By using the WordNet database, we can get most every pronoun, verb, adjective, etc in the English dictionary. While it's not everything, 
it for sure is a good basis and supplies plenty of room for learning. We can then do this one of two ways:
- have it analyze the database and acknowledge the types of speech. After this, we can feed it in sentences and create a collection of 
sentence structures.
- have it analyze the sentences first, referencing each word to the WordNet database for the part of speech. It'll then use machine 
learning to create a sequence of parts of speech (i.e.: `{ "pos": "adjective", "before": [ { "pos": "noun", "chance": 1 } ], "after": [] }`
 ).
 
### Emotion
We put emotion into everything we say, whether we notice it or not. So for this AI's reponses to seem realistic, it has to be able to also 
give emotion into what it's responses are. We could use a Sequence2Sequence model like with most things and have the emotion follow those 
sequences, but that contradicts how we humans feel emotions. If someone is yelling at us and immediately cut off to ask how the weather 
is, we rarely forget all of our previous emotions and start a new conversation. Instead of using that Seq2Seq model, why not give the AI 
an actual emotional value? We can have it analyze the emotion behind sentences and learn what the common emotional responses are. We can 
then have it retrofit the output with emotional modifiers or even have the output completely change based on the emotional value of the 
returned response. 

### Structs
```
// Grammar Solution #1
class SentenceAnalysisSolution1 {
  sentenceStructure: PartOfSpeech[];
}
// Grammar Solution #2
class SentenceAnalysisSolution2 {
  class PartOfSpeechAnalysis {
    partOfSpeech: PartOfSpeech;
    before: PartOfSpeech[];
    after: PartOfSpeech[];
  }
  
  posAnalysis: PartOfSpeechAnalysis[];
}

// Emotion Solution
class EmotionState {
  mood: int; // -10 being unhappy, 10 being happy
  trust: int; // -10 being skeptical, 10 being trustworthy
  anxiety: int; // -10 being anxious, 10 being calm. The more anxious it is, the higher the chance of countering the input emotion
}
```

