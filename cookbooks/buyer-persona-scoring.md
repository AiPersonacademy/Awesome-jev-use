# Cookbook: Buyer Persona Pain-Point & Intent Scoring

> **Problem**: Sifting through thousands of social threads or customer inquiries to extract actionable buyer persona profiles requires either expensive batch LLM summarization or brittle regex.
>
> **Solution**: Use Jev `Choice` and `Noul` to score user statements directly into structured buyer persona matrices (e.g. Pain Point Category, Budget Urgency, Purchase Readiness).

---

## Implementation (Python)

```python
from typesafe_sdk import TypeSafeClient, Choice, Noul

client = TypeSafeClient()

thread_comment = """
We've been burning 20 hours a week manually copy-pasting customer reviews from Reddit into spreadsheets. 
Every scraper we tried got IP-banned within 30 minutes. We have budget approved to buy a working solution today.
"""

state = {
    "text": thread_comment,
    "source": "r/entrepreneur",
    "target_product": "APA Scraping Intelligence Suite"
}

results = client.evaluate(
    state=state,
    questions=[
        Choice(
            id="primary_pain_point",
            description="What is the author's primary operational pain point?",
            options=[
                "AntiBotDetection_IPBans",
                "HighSoftwarePricing",
                "LackOfTechnicalExpertise",
                "UnrelatedDiscussion"
            ]
        ),
        Noul(
            id="has_immediate_buying_intent",
            description="Does the author indicate active budget approval or readiness to purchase a solution right now?"
        ),
        Choice(
            id="buyer_persona_segment",
            description="Which buyer persona category best describes this author?",
            options=[
                "Founder_Operator",
                "Enterprise_Architect",
                "Casual_Hobbyist",
                "Student_Researcher"
            ]
        )
    ]
)

print("Pain Point:", results["primary_pain_point"].choice)
print("Immediate Buying Intent Probability:", results["has_immediate_buying_intent"].probability)
print("Persona Segment:", results["buyer_persona_segment"].choice)
```
