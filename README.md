<!-- every visual on this page is a committed SVG under assets/ or GitHub-served. no third-party card services, nothing that can time out. -->

<div align="center">
  <a href="https://github.com/ThatOneSharpDude"><img src="assets/terminal.svg" width="100%" alt="Animated terminal session: fox boots his quant models, Poisson and Dixon-Coles fits stream by, a +3.4% EV edge is detected, the hedge locks, and the model log tails live"></a>
</div>

<p align="center">
  <a href="mailto:foxcamann@gmail.com"><img src="https://img.shields.io/badge/mail-foxcamann%40gmail.com-00ff9c?style=flat-square&labelColor=0d1117&logo=gmail&logoColor=00ff9c" alt="mail foxcamann@gmail.com"></a>
  <a href="https://github.com/ThatOneSharpDude"><img src="https://img.shields.io/badge/github-ThatOneSharpDude-00b4ff?style=flat-square&labelColor=0d1117&logo=github&logoColor=00b4ff" alt="github ThatOneSharpDude"></a>
  <img src="https://img.shields.io/badge/clv-validated-7b2ff7?style=flat-square&labelColor=0d1117" alt="clv validated">
</p>

<h3 align="center">I turn noisy data into provable edge.</h3>
<p align="center"><sub>Calibrated. Systematic. Relentless.</sub></p>

<br>

## `fox@edge:~$ whoami`

**Fox.** Quantitative sports bettor, AI automation architect, full-stack founder.
I price sports markets with real models, only bet when the number clears the vig, and grade every position against the closing line.

```diff
+ models that price the market before the market moves
+ edge detected [ok] :: hedge locked [ok] :: clv positive [ok]
- vibes, hunches, parlays    # deprecated
```

## `fox@edge:~$ htop -u fox`

<img src="assets/htop.svg" width="100%" alt="Process monitor: stateedge, quant-models, edge-terminal and jarvis running as processes with live CPU meters, a CLV drift sparkline averaging +2.1% and a hedge-depth ladder, uptime 1337 days, edge LIVE">

| pid | process | status | what it runs |
|--:|:--|:--|:--|
| `1337` | **StateEdge** | <img src="https://img.shields.io/badge/state-SHIPPING-00ff9c?style=flat-square&labelColor=0d1117" alt="shipping"> | US matched-betting SaaS. State x Book x Offer matrix, fee-aware hedge engine. |
| `2718` | **quant-models** | <img src="https://img.shields.io/badge/state-CALIBRATED-7b2ff7?style=flat-square&labelColor=0d1117" alt="calibrated"> | Poisson and Dixon-Coles for NHL, NBA, MLB, World Cup. CLV-validated. |
| `3141` | **edge-terminal** | <img src="https://img.shields.io/badge/state-SCANNING-00b4ff?style=flat-square&labelColor=0d1117" alt="scanning"> | Real-time +EV scanner. Books vs the sharp line, hedged on prediction markets. |
| `4242` | **jarvis** | <img src="https://img.shields.io/badge/state-LISTENING-e6edf3?style=flat-square&labelColor=0d1117" alt="listening"> | Local voice-driven agentic OS. The brain runs on my machine, not the cloud. |

<sub>All four in production. F9 kills variance. It has never worked, so the models handle it instead.</sub>

## `fox@edge:~$ cat ~/quant/pipeline.mmd`

```mermaid
%%{init: {"theme":"base","themeVariables":{"background":"#0d1117","mainBkg":"#161b22","primaryColor":"#161b22","primaryTextColor":"#e6edf3","primaryBorderColor":"#30363d","lineColor":"#00b4ff","fontFamily":"monospace","edgeLabelBackground":"#0d1117","clusterBkg":"#0d1117"}}}%%
flowchart LR
    A["ingest<br/>odds + stats + injuries"] --> B["models<br/>poisson / dixon-coles / kalman"]
    B --> C["calibration<br/>monte carlo, 50k paths"]
    C --> D{"edge clears<br/>the vig?"}
    D -- "no: pass" --> A
    D -- "yes" --> E["kelly sizing<br/>0.25x fractional"]
    E --> F["hedge lock<br/>fee-aware"]
    F --> G["clv check<br/>vs closing line"]
    G -. "feedback" .-> B
    style D stroke:#00ff9c,color:#00ff9c
    style E stroke:#00b4ff
    style G stroke:#7b2ff7
```

```python
# edge.config.py :: the whole philosophy in one dict
EDGE = {
    "pricing":    ["poisson", "dixon-coles"],   # goal and point distributions
    "state":      "kalman filter",              # team strength drift, tracked live
    "simulation": "monte carlo x 50_000",       # full outcome distributions, not point guesses
    "staking":    "fractional kelly (0.25x)",   # geometric growth, capped drawdown
    "validation": "closing line value",         # beat the close or it did not happen
}

assert EDGE["validation"] == "closing line value"   # no CLV, no edge, no bet
```

<details>
<summary><code>fox@edge:~$ cat sizing/kelly.py</code> <sub>:: the function that decides every stake</sub></summary>
<br>

```python
def kelly_stake(p_model: float, odds_dec: float, bankroll: float,
                fraction: float = 0.25, cap: float = 0.02) -> float:
    """Quarter-Kelly with a hard exposure cap. Edge or zero, never vibes."""
    b = odds_dec - 1.0                      # net payout per unit staked
    edge = p_model * odds_dec - 1.0         # expected value per unit
    if edge <= 0:
        return 0.0                          # no edge, no bet
    f_star = edge / b                       # full kelly fraction
    f = min(fraction * f_star, cap)         # fractional kelly, capped drawdown
    return round(bankroll * f, 2)

# >>> kelly_stake(p_model=0.52, odds_dec=2.06, bankroll=10_000)
# 167.92  :: quarter-kelly, under the 2% cap, sized to the edge
```

</details>

## `fox@edge:~$ which -a stack`

<p align="center">
  <a href="https://github.com/ThatOneSharpDude"><img src="https://skillicons.dev/icons?i=py,ts,js,react,nextjs,nodejs,tailwind,postgres,supabase,vercel,docker,git,linux,figma,discord&theme=dark&perline=15" alt="Python, TypeScript, JavaScript, React, Next.js, Node, Tailwind, Postgres, Supabase, Vercel, Docker, Git, Linux, Figma, Discord"></a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/pandas-0d1117?style=flat-square&logo=pandas&logoColor=00b4ff" alt="pandas">
  <img src="https://img.shields.io/badge/numpy-0d1117?style=flat-square&logo=numpy&logoColor=00ff9c" alt="numpy">
  <img src="https://img.shields.io/badge/stripe-0d1117?style=flat-square&logo=stripe&logoColor=9d5cff" alt="Stripe">
  <img src="https://img.shields.io/badge/claude-0d1117?style=flat-square&logo=anthropic&logoColor=e6edf3" alt="Anthropic Claude">
  <img src="https://img.shields.io/badge/sentry-0d1117?style=flat-square&logo=sentry&logoColor=9d5cff" alt="Sentry">
  <img src="https://img.shields.io/badge/discord_bots-0d1117?style=flat-square&logo=discord&logoColor=00b4ff" alt="Discord bots">
</p>

## `fox@edge:~$ tail -f telemetry.log`

<sub>Every commit is a data point. The models watch me too.</sub>

<img src="github-metrics.svg" width="100%" alt="GitHub metrics: header stats, 3D isometric contribution calendar, top languages and coding habits">

<img src="https://raw.githubusercontent.com/ThatOneSharpDude/ThatOneSharpDude/output/snake.svg" width="100%" alt="Contribution snake eating a year of commits">

## `fox@edge:~$ ping fox`

Signal beats noise. Two channels, both monitored.

<p align="center">
  <a href="mailto:foxcamann@gmail.com"><img src="https://img.shields.io/badge/mail-foxcamann%40gmail.com-00ff9c?style=for-the-badge&labelColor=0d1117&logo=gmail&logoColor=00ff9c" alt="mail foxcamann@gmail.com"></a>
  <a href="https://github.com/ThatOneSharpDude"><img src="https://img.shields.io/badge/github-ThatOneSharpDude-00b4ff?style=for-the-badge&labelColor=0d1117&logo=github&logoColor=00b4ff" alt="github ThatOneSharpDude"></a>
</p>

<br>

<div align="center">
  <img src="assets/ticker.svg" width="100%" alt="Scrolling tmux status line of model prices and locked hedges, then a typed prompt asks to explain the edge and the answer fades in: the house does not beat a man who does the math">
</div>
