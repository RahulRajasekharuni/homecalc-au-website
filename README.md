<!doctype html>
<html lang="en-AU">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <meta name="description" content="HomeCalc AU helps Australian property buyers understand purchase costs, repayments, rental returns and personal fit directly on property listings.">
  <meta name="theme-color" content="#2c6e49">
  <title>HomeCalc AU | Understand the real cost of a property</title>
  <style>
    :root {
      --green: #2c6e49;
      --green-dark: #1d4f34;
      --green-soft: #e9f3ee;
      --cream: #f8f7f2;
      --ink: #17231d;
      --text: #34443c;
      --muted: #6d7973;
      --line: #dce5e0;
      --amber: #b45309;
      --white: #ffffff;
      --shadow: 0 20px 55px rgba(23, 35, 29, 0.10);
    }

    * { box-sizing: border-box; }
    html { scroll-behavior: smooth; }
    body {
      margin: 0;
      background: var(--cream);
      color: var(--ink);
      font-family: Inter, ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
      line-height: 1.6;
    }

    a { color: inherit; }
    .wrap { width: min(1120px, calc(100% - 40px)); margin: 0 auto; }

    .site-header {
      position: sticky;
      top: 0;
      z-index: 20;
      border-bottom: 1px solid rgba(220, 229, 224, 0.9);
      background: rgba(248, 247, 242, 0.92);
      backdrop-filter: blur(14px);
    }

    .nav {
      min-height: 72px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 24px;
    }

    .brand {
      display: inline-flex;
      align-items: center;
      gap: 11px;
      color: var(--ink);
      font-weight: 800;
      text-decoration: none;
      letter-spacing: -0.02em;
    }

    .mark {
      display: grid;
      width: 38px;
      height: 38px;
      place-items: center;
      border-radius: 10px;
      background: var(--green);
      color: white;
      font-size: 13px;
      letter-spacing: 0;
    }

    .nav-links { display: flex; align-items: center; gap: 24px; }
    .nav-links a { color: var(--text); font-size: 14px; font-weight: 650; text-decoration: none; }
    .nav-links a:hover { color: var(--green); }

    .button {
      display: inline-flex;
      min-height: 46px;
      align-items: center;
      justify-content: center;
      padding: 0 20px;
      border: 1px solid var(--green);
      border-radius: 10px;
      background: var(--green);
      color: white;
      font-weight: 750;
      text-decoration: none;
      transition: transform .15s ease, background .15s ease;
    }
    .button:hover { background: var(--green-dark); transform: translateY(-1px); }
    .button.secondary { background: transparent; color: var(--green-dark); }
    .button.secondary:hover { background: var(--green-soft); }

    .hero {
      position: relative;
      overflow: hidden;
      padding: 92px 0 82px;
      background:
        radial-gradient(circle at 90% 10%, rgba(44, 110, 73, .14), transparent 30%),
        linear-gradient(180deg, #fbfaf6 0%, var(--cream) 100%);
    }

    .hero-grid { display: grid; grid-template-columns: 1.08fr .92fr; align-items: center; gap: 68px; }
    .eyebrow {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      margin-bottom: 20px;
      padding: 7px 11px;
      border: 1px solid #c8ded2;
      border-radius: 999px;
      background: var(--green-soft);
      color: var(--green-dark);
      font-size: 12px;
      font-weight: 800;
      letter-spacing: .08em;
      text-transform: uppercase;
    }

    h1 {
      max-width: 720px;
      margin: 0;
      font-size: clamp(44px, 6.2vw, 76px);
      line-height: 1.01;
      letter-spacing: -.055em;
    }

    .hero-copy > p {
      max-width: 660px;
      margin: 26px 0 30px;
      color: var(--text);
      font-size: 19px;
      line-height: 1.65;
    }

    .hero-actions { display: flex; flex-wrap: wrap; gap: 12px; }
    .microcopy { margin-top: 16px; color: var(--muted); font-size: 13px; }

    .product-card {
      position: relative;
      border: 1px solid var(--line);
      border-radius: 20px;
      background: var(--white);
      box-shadow: var(--shadow);
      overflow: hidden;
    }

    .product-head {
      display: flex;
      align-items: center;
      gap: 11px;
      padding: 18px 20px;
      border-bottom: 1px solid var(--line);
      font-weight: 800;
    }

    .mini-mark { display: grid; width: 30px; height: 30px; place-items: center; border-radius: 8px; background: var(--green); color: white; font-size: 10px; }
    .property { padding: 22px 22px 14px; }
    .property small { color: var(--muted); }
    .property h3 { margin: 3px 0; font-size: 20px; }
    .property strong { color: var(--green-dark); font-size: 17px; }
    .metric { display: flex; align-items: center; justify-content: space-between; gap: 20px; padding: 15px 22px; border-top: 1px solid var(--line); }
    .metric span { color: var(--muted); font-size: 13px; }
    .metric b { font-size: 15px; }
    .metric.total { background: var(--green-soft); }
    .metric.total b { color: var(--green-dark); font-size: 18px; }

    .trust-row {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      border-top: 1px solid var(--line);
      border-bottom: 1px solid var(--line);
      background: white;
    }
    .trust-item { padding: 22px; text-align: center; color: var(--text); font-size: 14px; font-weight: 700; }
    .trust-item + .trust-item { border-left: 1px solid var(--line); }

    section { padding: 86px 0; }
    .section-kicker { margin: 0 0 8px; color: var(--green); font-size: 13px; font-weight: 850; letter-spacing: .1em; text-transform: uppercase; }
    h2 { max-width: 760px; margin: 0; font-size: clamp(34px, 4.5vw, 50px); line-height: 1.12; letter-spacing: -.035em; }
    .section-lead { max-width: 720px; margin: 18px 0 0; color: var(--text); font-size: 17px; }

    .features { display: grid; grid-template-columns: repeat(3, 1fr); gap: 18px; margin-top: 42px; }
    .feature { min-height: 218px; padding: 26px; border: 1px solid var(--line); border-radius: 16px; background: white; }
    .feature-no { color: var(--green); font-size: 12px; font-weight: 850; letter-spacing: .08em; }
    .feature h3 { margin: 30px 0 9px; font-size: 20px; }
    .feature p { margin: 0; color: var(--text); font-size: 14px; }

    .how { background: var(--green-dark); color: white; }
    .how .section-kicker { color: #a9d3ba; }
    .how .section-lead { color: #dcebe2; }
    .steps { display: grid; grid-template-columns: repeat(3, 1fr); gap: 26px; margin-top: 44px; }
    .step { padding-top: 22px; border-top: 1px solid rgba(255,255,255,.22); }
    .step b { display: block; margin-bottom: 12px; color: #a9d3ba; font-size: 13px; }
    .step h3 { margin: 0 0 8px; font-size: 20px; }
    .step p { margin: 0; color: #dcebe2; font-size: 14px; }

    .pricing-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 18px; margin-top: 42px; align-items: stretch; }
    .price-card { position: relative; padding: 30px; border: 1px solid var(--line); border-radius: 17px; background: white; }
    .price-card.featured { border: 2px solid var(--green); box-shadow: var(--shadow); }
    .popular { position: absolute; top: -13px; right: 20px; padding: 5px 10px; border-radius: 999px; background: var(--green); color: white; font-size: 11px; font-weight: 850; text-transform: uppercase; }
    .plan { color: var(--green-dark); font-weight: 850; }
    .price { margin: 16px 0 4px; font-size: 35px; font-weight: 850; letter-spacing: -.04em; }
    .price small { color: var(--muted); font-size: 14px; font-weight: 600; letter-spacing: 0; }
    .price-card > p { min-height: 52px; color: var(--text); font-size: 14px; }
    .price-card ul { margin: 22px 0 0; padding: 0; list-style: none; }
    .price-card li { position: relative; margin: 11px 0; padding-left: 23px; color: var(--text); font-size: 14px; }
    .price-card li::before { content: "✓"; position: absolute; left: 0; color: var(--green); font-weight: 900; }

    .notice { margin-top: 26px; padding: 16px 18px; border-left: 4px solid var(--amber); border-radius: 8px; background: #fff7ed; color: #70420d; font-size: 13px; }

    .policies { background: #f1f5f2; }
    .policy-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 18px; margin-top: 40px; }
    details { border: 1px solid var(--line); border-radius: 14px; background: white; overflow: hidden; }
    summary { padding: 20px 22px; cursor: pointer; font-weight: 800; }
    details[open] summary { border-bottom: 1px solid var(--line); }
    .policy-body { padding: 2px 22px 22px; color: var(--text); font-size: 14px; }
    .policy-body h3 { margin: 22px 0 6px; color: var(--ink); font-size: 15px; }
    .policy-body p, .policy-body ul { margin-top: 7px; }

    .support-card {
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 30px;
      padding: 38px;
      border-radius: 18px;
      background: white;
      box-shadow: var(--shadow);
    }
    .support-card h2 { font-size: 32px; }
    .support-card p { margin: 8px 0 0; color: var(--text); }

    footer { padding: 32px 0 42px; border-top: 1px solid var(--line); }
    .footer-row { display: flex; justify-content: space-between; gap: 24px; color: var(--muted); font-size: 12px; }
    .footer-links { display: flex; flex-wrap: wrap; gap: 18px; }
    .footer-links a { text-decoration: none; }

    @media (max-width: 880px) {
      .hero-grid { grid-template-columns: 1fr; gap: 44px; }
      .features, .pricing-grid, .steps { grid-template-columns: 1fr; }
      .trust-row { grid-template-columns: 1fr 1fr; }
      .trust-item:nth-child(3) { border-left: 0; border-top: 1px solid var(--line); }
      .trust-item:nth-child(4) { border-top: 1px solid var(--line); }
      .policy-grid { grid-template-columns: 1fr; }
    }

    @media (max-width: 620px) {
      .wrap { width: min(100% - 28px, 1120px); }
      .nav-links a:not(.button) { display: none; }
      .hero { padding: 64px 0; }
      section { padding: 66px 0; }
      .trust-row { grid-template-columns: 1fr; }
      .trust-item + .trust-item { border-left: 0; border-top: 1px solid var(--line); }
      .support-card, .footer-row { align-items: flex-start; flex-direction: column; }
      .hero-actions .button { width: 100%; }
      .metric { align-items: flex-start; flex-direction: column; gap: 3px; }
    }
  </style>
</head>
<body>
  <header class="site-header">
    <div class="wrap nav">
      <a class="brand" href="#top"><span class="mark">HC</span><span>HomeCalc AU</span></a>
      <nav class="nav-links" aria-label="Primary navigation">
        <a href="#features">Features</a>
        <a href="#pricing">Pricing</a>
        <a href="#policies">Policies</a>
        <a class="button" href="#support">Contact support</a>
      </nav>
    </div>
  </header>

  <main id="top">
    <div class="hero">
      <div class="wrap hero-grid">
        <div class="hero-copy">
          <div class="eyebrow">Built for Australian property buyers</div>
          <h1>Know what a property will actually cost you.</h1>
          <p>HomeCalc AU is a Chrome extension that turns residential listings into practical owner and investor estimates, so you can compare the costs, returns and personal fit before making your next move.</p>
          <div class="hero-actions">
            <a class="button" href="#pricing">See plans</a>
            <a class="button secondary" href="#how">How it works</a>
          </div>
          <div class="microcopy">Supports listings on realestate.com.au and Domain across all Australian states and territories.</div>
        </div>

        <div class="product-card" aria-label="Example HomeCalc property summary">
          <div class="product-head"><span class="mini-mark">HC</span> Property snapshot</div>
          <div class="property">
            <small>Example residential property</small>
            <h3>Your shortlisted home</h3>
            <strong>A$910,000 purchase price</strong>
          </div>
          <div class="metric"><span>Estimated cash required</span><b>Calculated for your inputs</b></div>
          <div class="metric"><span>Mortgage repayment</span><b>Your loan, rate and term</b></div>
          <div class="metric"><span>Owner or investor view</span><b>Separate comparisons</b></div>
          <div class="metric total"><span>Personal Fit score</span><b>Your targets, not market stars</b></div>
        </div>
      </div>
    </div>

    <div class="trust-row" aria-label="Product coverage">
      <div class="trust-item">All 8 states and territories</div>
      <div class="trust-item">Owner and investor modes</div>
      <div class="trust-item">Transparent editable assumptions</div>
      <div class="trust-item">Estimates clearly labelled</div>
    </div>

    <section id="features">
      <div class="wrap">
        <p class="section-kicker">One clearer view</p>
        <h2>Move beyond the listing price.</h2>
        <p class="section-lead">HomeCalc brings the figures scattered across calculators, notes and property tabs into one consistent comparison.</p>

        <div class="features">
          <article class="feature"><span class="feature-no">01 · PURCHASE</span><h3>Upfront costs</h3><p>Estimate deposit, transfer duty, registration fees, conveyancing, inspections, LMI and the total cash required.</p></article>
          <article class="feature"><span class="feature-no">02 · MORTGAGE</span><h3>Loan repayments</h3><p>Model principal-and-interest or interest-only repayments using your loan amount, interest rate and term.</p></article>
          <article class="feature"><span class="feature-no">03 · INVESTOR</span><h3>Rental performance</h3><p>Compare gross and net yield, vacancy, management costs and nationally comparable after-interest cash flow.</p></article>
          <article class="feature"><span class="feature-no">04 · COMPARE</span><h3>Separate shortlists</h3><p>Keep owner and investor comparisons separate, with table, card, sorting and CSV export views.</p></article>
          <article class="feature"><span class="feature-no">05 · PERSONAL FIT</span><h3>Your priorities</h3><p>Score properties against your chosen walking time, commute, schools, property type and other personal targets.</p></article>
          <article class="feature"><span class="feature-no">06 · CONTROL</span><h3>Honest assumptions</h3><p>Edit missing facts such as year built, strata fees and walking time rather than relying on invented data.</p></article>
        </div>
      </div>
    </section>

    <section class="how" id="how">
      <div class="wrap">
        <p class="section-kicker">How it works</p>
        <h2>From listing to shortlist in three steps.</h2>
        <p class="section-lead">The extension appears alongside supported property listings and keeps every estimate adjustable.</p>
        <div class="steps">
          <div class="step"><b>STEP 1</b><h3>Open a listing</h3><p>Visit a residential listing on realestate.com.au or Domain and open the HomeCalc panel.</p></div>
          <div class="step"><b>STEP 2</b><h3>Add your assumptions</h3><p>Choose owner or investor mode, then review financing, costs, rent and personal preferences.</p></div>
          <div class="step"><b>STEP 3</b><h3>Compare your shortlist</h3><p>Save suitable properties and compare them using consistent targets and visible data coverage.</p></div>
        </div>
      </div>
    </section>

    <section id="pricing">
      <div class="wrap">
        <p class="section-kicker">Simple pricing</p>
        <h2>Start free. Upgrade while you are actively searching.</h2>
        <p class="section-lead">All prices are in Australian dollars. Paid access is attached to your HomeCalc account.</p>

        <div class="pricing-grid">
          <article class="price-card">
            <div class="plan">Free</div>
            <div class="price">A$0</div>
            <p>For getting started with a small number of properties.</p>
            <ul><li>3 new property analyses per calendar month</li><li>Revisit previously analysed properties</li><li>Core owner and investor calculations</li></ul>
          </article>

          <article class="price-card featured">
            <span class="popular">Most flexible</span>
            <div class="plan">Buyer Pro</div>
            <div class="price">A$19.99 <small>/ month</small></div>
            <p>For buyers who want ongoing access throughout their search.</p>
            <ul><li>Unlimited property analyses</li><li>Owner and investor shortlist comparisons</li><li>CSV export</li><li>Cancel at any time</li></ul>
          </article>

          <article class="price-card">
            <div class="plan">House Hunter Pass</div>
            <div class="price">A$39 <small>one time</small></div>
            <p>For a focused property search without a recurring subscription.</p>
            <ul><li>90 days of unlimited access</li><li>Owner and investor shortlist comparisons</li><li>CSV export</li><li>No automatic renewal</li></ul>
          </article>
        </div>

        <div class="notice">HomeCalc provides estimates for general information only. It does not provide financial, legal, tax, lending or property-investment advice. Always confirm important figures with the relevant authority or a qualified professional.</div>
      </div>
    </section>

    <section class="policies" id="policies">
      <div class="wrap">
        <p class="section-kicker">Customer information</p>
        <h2>Clear policies, without the fine-print maze.</h2>
        <p class="section-lead">Last updated 18 August 2026.</p>

        <div class="policy-grid">
          <details open>
            <summary>Cancellation and refund policy</summary>
            <div class="policy-body">
              <h3>Buyer Pro subscription</h3>
              <p>You may cancel at any time through the billing management link in HomeCalc. Cancellation stops future renewals and access continues until the end of the paid billing period. Partial billing periods are not normally prorated.</p>
              <h3>House Hunter Pass</h3>
              <p>The pass is a one-time purchase, does not renew automatically and provides 90 days of access. Refund requests made within 7 days will be considered where the pass has not been substantially used.</p>
              <h3>Problems with the service</h3>
              <p>If a technical problem prevents you from receiving the access purchased and we cannot resolve it within a reasonable time, contact support to request an appropriate remedy.</p>
              <p>Nothing in this policy excludes rights or remedies that cannot be excluded under the Australian Consumer Law.</p>
            </div>
          </details>

          <details>
            <summary>Privacy summary</summary>
            <div class="policy-body">
              <p>HomeCalc stores your listing analyses, manual inputs, preferences, notes and shortlist information to provide the extension’s features. Much of this information is stored on your device. When you sign in, account details, plan status, usage counts and synced shortlist information may be stored securely by our service providers.</p>
              <p>Payment details are processed by Stripe. HomeCalc does not receive or store your complete card number. Listing pages are read by the extension to produce the analysis; HomeCalc does not sell personal information or collect a general history of websites you visit.</p>
              <p>You can export or remove local HomeCalc data from the extension settings. Contact support for account or privacy requests. Information may be retained where reasonably necessary for security, dispute resolution, legal or accounting obligations.</p>
            </div>
          </details>

          <details>
            <summary>Terms of use</summary>
            <div class="policy-body">
              <p>HomeCalc AU is a decision-support tool for adults considering Australian residential property. By using it, you agree to provide lawful inputs, keep your account secure and avoid attempting to interfere with or misuse the service.</p>
              <p>Calculations depend on listing information, user inputs, assumptions and rate tables that may be incomplete, approximate or change over time. Results are not valuations, lending approvals, forecasts or professional advice. You remain responsible for checking figures and making your own decisions.</p>
              <p>We aim to keep HomeCalc available and accurate, but do not promise uninterrupted availability or that every portal listing will contain every required fact. To the extent permitted by law, liability is limited to the remedies required under applicable consumer law.</p>
            </div>
          </details>

          <details>
            <summary>Support and disputes</summary>
            <div class="policy-body">
              <p>For account access, billing, cancellation, refund or privacy questions, contact us using the support email below. Include the email address associated with your HomeCalc account, but never send passwords or complete payment-card details.</p>
              <p>We will acknowledge customer enquiries as soon as reasonably practicable and work in good faith to resolve billing disputes. If a payment appears incorrect, please contact us before opening a payment dispute so we have an opportunity to investigate.</p>
            </div>
          </details>
        </div>
      </div>
    </section>

    <section id="support">
      <div class="wrap">
        <div class="support-card">
          <div><p class="section-kicker">Support</p><h2>Need help with HomeCalc?</h2><p>Account, billing and product questions are welcome.</p></div>
          <!-- Replace YOUR_SUPPORT_EMAIL before publishing. -->
          <a class="button" href="mailto:YOUR_SUPPORT_EMAIL">YOUR_SUPPORT_EMAIL</a>
        </div>
      </div>
    </section>
  </main>

  <footer>
    <div class="wrap footer-row">
      <div>© 2026 HomeCalc AU. All rights reserved.</div>
      <div class="footer-links"><a href="#pricing">Pricing</a><a href="#policies">Refunds</a><a href="#policies">Privacy</a><a href="#policies">Terms</a><a href="#support">Support</a></div>
    </div>
  </footer>
</body>
</html>
