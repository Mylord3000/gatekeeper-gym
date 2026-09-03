# Gatekeeper Gym

Voice-to-voice training simulator for getting past corporate front desks. You speak into the mic; a harsh, realistic receptionist answers back in a real voice; your delivery is measured; a coach tears the transcript apart afterwards.

Built for founder customer-discovery practice: the win condition is being routed to a specific person (a name, a direct extension, or an internal call). A generic "email info@" is a loss.

## How it works

- Your voice in: Chrome's built-in speech recognition transcribes you; your audio is also recorded locally so you can replay your own tone.
- - The gatekeeper: Claude (Anthropic API) plays the receptionist. Difficulty D2-D5, from bored professional to a two-sentence-attention-span worst case that ends the conversation after four weak turns. Her default wall: "you need to have a meeting planned."
  - - Her voice out: ElevenLabs TTS (Flash v2.5). Falls back to the browser's built-in voice if no key is set.
    - - Delivery metrics, computed locally per turn: words/minute, filler words, long pauses, loudness steadiness.
      - - Coach mode: after a session, Claude scores five axes (first-5-seconds clarity, specificity, calm under refusal, converting a no into a name, exit quality), quotes the turn that decided the outcome, writes the stronger line verbatim, and assigns one drill.
        - - Scenarios: 15 preloaded Finnish industrial lobbies, each with a hidden "right role to ask for."
         
          - ## Setup
         
          - 1. Open the hosted page (GitHub Pages) or index.html locally in Chrome.
            2. 2. Paste your Anthropic API key and (optionally) ElevenLabs API key. Keys are stored in your browser's localStorage only and sent directly to the respective APIs. There is no backend.
               3. 3. Load voices, pick the most clipped businesslike one, pick a lobby and difficulty, hit Start session, and speak.
                 
                  4. If the mic is blocked when opening as a local file, serve it with: python3 -m http.server
                 
                  5. ## Costs
                 
                  6. Per 10-minute session: a cent or two of Claude API usage and roughly 2k ElevenLabs credits. Browser TTS fallback is free.
                 
                  7. ## Privacy
                 
                  8. No server, no analytics. Audio never leaves your machine except that Chrome's speech recognition uses Google's service for transcription, transcript text goes to Anthropic, and the gatekeeper's lines go to ElevenLabs.
                 
                  9. ## License
                 
                  10. MIT
                  11. 
