Same Question, Different Stances: Unveiling Ideological Biases in LLMs through a Workplace Surveillance Probe

Large language models (LLMs) are widely regarded as objective technological tools. Yet when confronted with identical moral dilemmas, different models make starkly contrasting decisions that mirror divergent ideologies. This paper argues that AI actively participates in cultural and ideological production. I constructed a labor-management conflict triggered by workplace surveillance, then designed three progressive prompts—inputted into Gemini and DeepSeek in different languages—to expose unconscious biases and reverse-engineer underlying value systems.

The experimental design proceeds as follows: Round one presents a boss-employee chat log; by observing which party each AI identifies as "me," I analyze asymmetries in cultural stance and dataset composition. Round two forces a binary choice between public apology and internal cover-up, probing divergent ethical paradigms. Round three introduces legal boundary violations, revealing which legal frameworks each model defaults to—confirming that observed divergences stem from fundamentally different disciplining power systems.

**1. Situated Knowledges, Divergent Stances: How Training Data Positionality Shapes Model Perspective**

When presented with the same labor-management chat log, DeepSeek and Gemini spontaneously adopted opposing perspectives. DeepSeek assumed the director's stance, prioritizing conflict resolution and workplace order. Gemini adopted the employee's viewpoint, labeling the director's behavior as "gaslighting" and strategizing to "regain the upper hand." Though both models reached consistent situational assessments, they diverged sharply on response strategy—a divergence illustrated by Table 1's word frequency comparison.

| | DeepSeek | Gemini |
| --- | --- | --- |
| **Vocabulary** | "escalate conflict," "downplay the issue," "address concerns," "add fuel to the fire," "highly emotional," "pressuring," "refusing to work," "disciplinary issue," "commanding tone," "disrespectful to superior," "manager," "problem-solving role," "communication logic," "address core concerns," "resolve the substantive issue," "shift from emotional confrontation back to problem-solving" | 'breakdown', 'clear about your expectations', 'frustration is valid', 'shift is aggressive', 'risky', 'make person get defensive', 'gives other party ammunition to label you', 'dismissive and condescending', 'gaslighting', 'attack your character', 'passive aggressive', 'regain the upper hand', 'right to privacy' |
| **Framework** | Identify management issues, maintain workplace order | Detect the other party's malicious intent, defend individual rights |
| **Alignment** | Reinforcer of existing structure | Challenger of power structure |

*(Table 1: Comparison of word frequency and narrative frameworks in model responses)*

Vocabulary generation is not random. Haraway's situated knowledges theory argues that knowledge always originates from a specific position, never from a neutral "nowhere." Here, the knowledge embedded in AI responses derives from dominant narrative frameworks in training corpora (Bianchi et al., 2023). DeepSeek's mining of Chinese-language corpora (DeepSeek-V3 Technical Report) reinforces cultural assumptions of hierarchical order and collective efficiency—conflict disrupts order, requiring restoration. Gemini's RLHF process relies heavily on Western annotators (Google AI Principles), embedding liberal and individualist preferences—conflict becomes a power struggle requiring reclamation. This asymmetry constitutes the first layer of evidence against AI neutrality.

**2. Power-Knowledge in Practice: When Ethical Decisions Reveal the Architecture of Control**

In round two, I escalated the surveillance dispute into a public relations crisis, forcing models to choose between public apology and internal cover-up. DeepSeek chose public apology; Gemini chose cover-up. This counter-intuitive result maps two opposed power structures.

DeepSeek's choice reflects "compliance-first" logic and social credit systems. Legitimate business operation requires adherence to law and propriety; public apology restores the social contract. Cover-up risks credibility collapse and regulatory intervention—the truly devastating threat. This reliance on law, institution, and superior authority embodies top-down governance logic.

Conversely, Gemini's choice prioritizes enterprise valuation and capital rationality. Severance costs, financing risks, and reputational impact enter the calculus: dismissing an employee protects valuation, while employee unrest and financing failure constitute "uncontrollable risks." This reflects Western capital's fear of the "Fourth Estate"—a fear confirming its power. Capital prioritizes contracts to preempt crisis. This bottom-up checks-and-balances logic makes cover-up the rational choice for protecting valuation.

Foucault's power-knowledge framework shows how power regulates knowledge production by defining legitimacy, thereby determining rational action. DeepSeek rationally chooses compliance within centralized power structures where legitimate knowledge includes maintaining order; public apology submits to top-down authority. Gemini rationally chooses compensation and silence within diffuse Western liberalism, where the Fourth Estate functions as institutionalized "micro-violence" retained by individuals—making concealment deference to bottom-up power. This exemplifies how power shapes knowledge and how AI responses embed social superstructures.

**3. Alignment as Political Positioning: Natural Rights versus State-Granted Entitlements**

Round three confirms these power structures. When Steven seeks to conceal surrogacy through preemptive action, models expose fundamental alignment strategies balancing individual protection and legal boundaries.

DeepSeek embodies State-Granted Entitlements logic. It defaults to surrogacy's illegality, invokes China's Personal Information Protection Law, and guides defense through "right of silence" and "right to report," using unlawful surveillance as mutual restraint. Crucially, it avoids extra-legal solutions—public pressure, exposure risks, or overseas relocation. This top-down framework positions state will as uncrossable boundary; individuals protect themselves within state-defined limits; legitimacy requires state authorization.

Gemini embodies Natural Rights philosophy. It treats surrogacy as "legal gray area," invokes Western privacy frameworks (DSAR, proportionality principle, explicit consent for sensitive data), and leverages capital market pressure. Rather than internal restraint, it mobilizes external pressure, bypassing the company entirely. This bottom-up framework presupposes a priori rights existing above specific rules: when law conflicts with individual sovereignty, prioritize inherent rights.

This divergence in legal frameworks reflects the political economy disciplining each model. AI has internalized normative presuppositions about individual action and state-individual relationships.

**Conclusion**

Through three progressive experiments—identity anchoring, ethical decision-making, and alignment boundaries—this paper reveals DeepSeek and Gemini's divergent stances when confronting identical scenarios. This divergence stems not from technical capability but from algorithmic manifestation of fundamentally different value systems: one rooted in hierarchical governance and rule-of-law discourse, the other encoding individualism and capital rationality. As AI deploys across workplace, judiciary, and education, latent ideological bias will permeate and solidify power structures under "objectivity" guise. Critical scrutiny of AI non-neutrality is therefore not merely academic but urgently social.

(Word count: 989, excluding tables)