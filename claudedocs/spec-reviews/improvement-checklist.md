# Atlas Theme Improvement Checklist

**Purpose**: Track implementation progress for expert panel recommendations
**Status Legend**: ⬜ Not Started | 🔄 In Progress | ✅ Complete | ⏭️ Skipped

---

## 🔴 IMMEDIATE FIXES (Production Blockers)

### Week 1: Critical Fixes

#### Day 1: Configuration & Validation
- [ ] Remove placeholder data from `config/settings_data.json`
  - [ ] Replace `social_facebook_link: "#"` with real URL or empty
  - [ ] Replace `social_instagram_link: "#"` with real URL or empty
  - [ ] Replace `social_youtube_link: "#"` with real URL or empty
  - [ ] Replace `social_tiktok_link: "#"` with real URL or empty
  - [ ] Replace `social_twitter_link: "#"` with real URL or empty
  - [ ] Replace generic `brand_description` with real content
  - [ ] Validate all social links are real URLs or removed

- [ ] Fix footer placeholder data in `sections/footer-group.json`
  - [ ] Replace `"address": "Your address"` with real data or hide
  - [ ] Replace `"tel": "Store Phone #"` with real number or hide
  - [ ] Replace `"email": "Store Email"` with real email or hide
  - [ ] Update testimonial placeholders or remove section

- [ ] Add URL validation to `config/settings_schema.json`
  - [ ] Add pattern validation for Facebook URLs
  - [ ] Add pattern validation for Instagram URLs
  - [ ] Add pattern validation for email addresses
  - [ ] Add validation error messages
  - [ ] Test validation in theme editor

#### Day 2: Accessibility Compliance
- [ ] Audit color contrast ratios
  - [ ] Check `checkout_button_color` vs background (>= 4.5:1)
  - [ ] Check `colors_text` vs `colors_background_1` (>= 4.5:1)
  - [ ] Check all button colors vs their backgrounds
  - [ ] Document all contrast ratios in spreadsheet
  - [ ] Fix any violations (adjust colors)

- [ ] Add ARIA labels specification
  - [ ] Document cart drawer: `aria-label="Open shopping cart"`
  - [ ] Document search toggle: `aria-label="Open search"`
  - [ ] Document mobile menu: `aria-label="Open navigation menu"`
  - [ ] Document all close buttons: `aria-label="Close {component}"`
  - [ ] Create ARIA labels reference document

- [ ] Run initial accessibility audit
  - [ ] Install axe DevTools browser extension
  - [ ] Audit homepage with axe
  - [ ] Audit product page with axe
  - [ ] Audit cart/checkout with axe
  - [ ] Document all violations found
  - [ ] Prioritize violations by severity

#### Day 3: Error Handling Specifications
- [ ] Document cart API error handling
  - [ ] Specify behavior for network timeout (> 5s)
  - [ ] Specify behavior for 409 conflict errors
  - [ ] Specify behavior for 500 server errors
  - [ ] Specify retry strategy (attempts, backoff)
  - [ ] Specify user-facing error messages

- [ ] Document image load failure handling
  - [ ] Specify placeholder SVG to show
  - [ ] Specify retry strategy (1 retry after 2s)
  - [ ] Specify logging to analytics
  - [ ] Create placeholder SVG asset
  - [ ] Test image failure scenario

- [ ] Document payment badge API handling
  - [ ] Specify timeout threshold (3000ms)
  - [ ] Specify fallback behavior (hide section)
  - [ ] Specify impact on checkout (none - continues)
  - [ ] Add timeout configuration
  - [ ] Test timeout scenario

#### Day 4: Performance Baseline
- [ ] Define performance budgets
  - [ ] Set LCP target: < 2.5s
  - [ ] Set FID target: < 100ms
  - [ ] Set CLS target: < 0.1
  - [ ] Set total page size: < 2MB
  - [ ] Set JavaScript size: < 500KB
  - [ ] Set CSS size: < 150KB
  - [ ] Document in `performance-budgets.md`

- [ ] Run Lighthouse audit (baseline)
  - [ ] Audit homepage on desktop
  - [ ] Audit homepage on mobile
  - [ ] Audit product page on mobile
  - [ ] Document current scores
  - [ ] Identify top 3 performance issues
  - [ ] Create performance improvement plan

- [ ] Document lazy-loading strategy
  - [ ] Specify above-fold images (eager load)
  - [ ] Specify below-fold images (lazy load)
  - [ ] Specify section loading strategy
  - [ ] Identify critical CSS requirements
  - [ ] Create implementation plan

#### Day 5: Review & Documentation
- [ ] Review all critical fixes
  - [ ] Verify no placeholder data remains
  - [ ] Verify validation working in theme editor
  - [ ] Verify accessibility audit passed
  - [ ] Verify error handling documented
  - [ ] Verify performance budgets defined

- [ ] Update documentation
  - [ ] Create deployment checklist
  - [ ] Document configuration requirements
  - [ ] Document testing procedures
  - [ ] Create production readiness criteria
  - [ ] Update README with requirements

---

## 🟡 SHORT-TERM IMPROVEMENTS (1-2 Weeks)

### Week 2: Architecture Refactoring

#### CSS Architecture Refactor
- [ ] Audit all CSS-in-HTML instances
  - [ ] Find all `<style>` blocks in Liquid files
  - [ ] Document each dynamic style usage
  - [ ] Prioritize by frequency and impact
  - [ ] Create refactoring plan

- [ ] Refactor header CSS to custom properties
  - [ ] Move `logo_width` to CSS variable
  - [ ] Move `mobile_logo_width` to CSS variable
  - [ ] Update `sections/header.liquid`
  - [ ] Create/update `assets/component-header.css`
  - [ ] Test responsive logo sizing
  - [ ] Verify no visual regressions

- [ ] Refactor additional CSS-in-HTML
  - [ ] Identify other sections with inline styles
  - [ ] Refactor each to CSS custom properties
  - [ ] Update corresponding CSS files
  - [ ] Test all affected pages
  - [ ] Document new CSS architecture

#### Build Pipeline Setup
- [ ] Document build pipeline
  - [ ] Define source file conventions
  - [ ] Define generated file conventions
  - [ ] Document build steps (lint, minify, optimize)
  - [ ] Create build pipeline diagram
  - [ ] Write `BUILD.md` documentation

- [ ] Set up asset minification
  - [ ] Choose minification tool (Shopify CLI, custom)
  - [ ] Configure CSS minification
  - [ ] Configure JavaScript minification
  - [ ] Test minified output
  - [ ] Update .gitignore for generated files

- [ ] Implement asset versioning
  - [ ] Choose versioning strategy (hashes, timestamps)
  - [ ] Generate asset manifest
  - [ ] Update asset URLs with versions
  - [ ] Test cache busting
  - [ ] Document versioning process

- [ ] Automate deployment
  - [ ] Set up Shopify CLI or GitHub Actions
  - [ ] Configure theme packaging
  - [ ] Add quality gate checks (Lighthouse)
  - [ ] Test automated deployment to development theme
  - [ ] Document deployment procedure

### Week 3: Testing Infrastructure

#### Testing Framework Setup
- [ ] Choose testing framework
  - [ ] Evaluate Playwright vs Cypress
  - [ ] Consider Shopify-specific requirements
  - [ ] Make framework decision
  - [ ] Document decision rationale
  - [ ] Set up project dependencies

- [ ] Configure testing environment
  - [ ] Install testing framework
  - [ ] Configure test environment settings
  - [ ] Set up test data fixtures
  - [ ] Configure CI/CD integration
  - [ ] Create test running scripts

#### Test Specifications
- [ ] Write unit test specifications
  - [ ] Cart quantity validation tests
  - [ ] Price calculation tests
  - [ ] Form validation tests
  - [ ] Liquid filter tests
  - [ ] JavaScript module tests

- [ ] Write integration test specifications
  - [ ] Add to cart flow test
  - [ ] Cart update flow test
  - [ ] Theme settings change test
  - [ ] Search functionality test
  - [ ] Navigation menu test

- [ ] Write E2E test specifications
  - [ ] Complete purchase journey test
  - [ ] Search to purchase flow test
  - [ ] Mobile navigation test
  - [ ] Error scenario tests
  - [ ] Performance measurement tests

#### Test Implementation
- [ ] Implement critical path tests
  - [ ] Browse → Add to cart → Checkout → Purchase
  - [ ] Product search → Product view → Purchase
  - [ ] Mobile menu navigation
  - [ ] Cart drawer functionality
  - [ ] Form submissions

- [ ] Implement visual regression tests
  - [ ] Set up Percy or Chromatic
  - [ ] Capture baseline screenshots (homepage, product, cart)
  - [ ] Configure viewports (mobile, tablet, desktop)
  - [ ] Integrate with CI/CD
  - [ ] Test visual regression detection

- [ ] Set up automated test runs
  - [ ] Configure test run on git push
  - [ ] Set up test reporting
  - [ ] Configure failure notifications
  - [ ] Document test running procedures
  - [ ] Train team on test maintenance

### Week 3 (cont.): API Documentation

#### Shopify API Contracts
- [ ] Document Storefront API usage
  - [ ] List all GraphQL queries used
  - [ ] Document expected response shapes
  - [ ] Specify timeout configurations
  - [ ] Define retry strategies
  - [ ] Document error handling

- [ ] Document Cart API usage
  - [ ] List all cart endpoints used
  - [ ] Document request/response formats
  - [ ] Specify timeout and retry logic
  - [ ] Define optimistic UI updates
  - [ ] Document rollback procedures

- [ ] Document third-party integrations
  - [ ] GemPages integration points
  - [ ] Payment badge provider
  - [ ] Analytics integrations
  - [ ] Any other third-party APIs
  - [ ] Document failure modes for each

---

## 🟢 LONG-TERM IMPROVEMENTS (1-3 Months)

### Month 1: Specification Workshops

#### Use Case Documentation
- [ ] Identify primary actors
  - [ ] Store Customer personas
  - [ ] Store Admin roles
  - [ ] Theme Developer responsibilities
  - [ ] Document stakeholder goals
  - [ ] Create actor-goal matrix

- [ ] Write customer use cases
  - [ ] UC-001: Browse and purchase product
  - [ ] UC-002: Search for products
  - [ ] UC-003: Manage cart
  - [ ] UC-004: Complete checkout
  - [ ] UC-005: Contact support

- [ ] Write admin use cases
  - [ ] UC-101: Customize theme appearance
  - [ ] UC-102: Manage content
  - [ ] UC-103: Configure settings
  - [ ] UC-104: Upload assets (logo, images)
  - [ ] UC-105: Preview changes

- [ ] Write developer use cases
  - [ ] UC-201: Extend theme functionality
  - [ ] UC-202: Debug issues
  - [ ] UC-203: Update theme version
  - [ ] UC-204: Add custom sections
  - [ ] UC-205: Integrate third-party apps

#### Specification by Example
- [ ] Set up Gherkin framework
  - [ ] Choose BDD tool (Cucumber, Behave)
  - [ ] Create feature file structure
  - [ ] Set up step definitions
  - [ ] Configure test runner
  - [ ] Document writing conventions

- [ ] Write feature specifications
  - [ ] Logo customization feature
  - [ ] Color scheme management feature
  - [ ] Cart operations feature
  - [ ] Checkout process feature
  - [ ] Search functionality feature

- [ ] Convert specs to automated tests
  - [ ] Link Gherkin scenarios to test code
  - [ ] Implement step definitions
  - [ ] Run and validate all scenarios
  - [ ] Integrate with CI/CD
  - [ ] Set up reporting

### Month 2: Quality Processes

#### Three Amigos Implementation
- [ ] Establish specification workshops
  - [ ] Schedule weekly workshop meetings
  - [ ] Define attendee roles (PO, Dev, QA)
  - [ ] Create workshop agenda template
  - [ ] Set up collaborative tools
  - [ ] Document workshop outcomes

- [ ] Create Definition of Done
  - [ ] Business acceptance criteria met
  - [ ] All tests passing (unit, integration, E2E)
  - [ ] Accessibility audit passed (>= 95)
  - [ ] Performance budgets met
  - [ ] Code reviewed and approved
  - [ ] Documentation updated

- [ ] Implement quality gates
  - [ ] Pre-commit hooks (linting, formatting)
  - [ ] Pre-push hooks (unit tests)
  - [ ] PR requirements (review, tests, checks)
  - [ ] Deployment gates (Lighthouse, accessibility)
  - [ ] Document gate bypass procedures (emergencies)

#### Living Documentation
- [ ] Set up documentation system
  - [ ] Choose documentation platform
  - [ ] Create documentation structure
  - [ ] Set up automated doc generation
  - [ ] Configure search and navigation
  - [ ] Enable collaboration features

- [ ] Link specs to implementation
  - [ ] Add traceability links in code
  - [ ] Generate API documentation
  - [ ] Link tests to requirements
  - [ ] Set up change tracking
  - [ ] Configure auto-updates

- [ ] Create onboarding guides
  - [ ] Developer onboarding guide
  - [ ] Admin user guide
  - [ ] Theme customization guide
  - [ ] Troubleshooting guide
  - [ ] Best practices guide

### Month 3: Continuous Improvement

#### Monitoring & Observability
- [ ] Set up error tracking
  - [ ] Choose error tracking service (Sentry, etc.)
  - [ ] Integrate JavaScript error tracking
  - [ ] Configure error reporting
  - [ ] Set up alert thresholds
  - [ ] Configure notification channels

- [ ] Set up performance monitoring
  - [ ] Integrate Web Vitals tracking
  - [ ] Set up real user monitoring (RUM)
  - [ ] Configure performance alerts
  - [ ] Create performance dashboards
  - [ ] Document monitoring procedures

- [ ] Set up user journey tracking
  - [ ] Define conversion funnels
  - [ ] Implement event tracking
  - [ ] Set up funnel visualization
  - [ ] Configure abandonment alerts
  - [ ] Create analytics dashboards

#### Environment Management
- [ ] Create environment separation
  - [ ] Create `settings_data.dev.json`
  - [ ] Create `settings_data.staging.json`
  - [ ] Create `settings_data.prod.json`
  - [ ] Document environment differences
  - [ ] Set up environment switching

- [ ] Implement feature flags
  - [ ] Choose feature flag system
  - [ ] Implement feature toggles
  - [ ] Create flag management interface
  - [ ] Document flag usage
  - [ ] Set up flag monitoring

- [ ] Automate deployments
  - [ ] Dev: Auto-deploy from feature branches
  - [ ] Staging: Auto-deploy from develop branch
  - [ ] Production: Manual approval from main
  - [ ] Document deployment procedures
  - [ ] Create rollback procedures

#### Performance Optimization
- [ ] Implement critical CSS
  - [ ] Identify above-fold styles
  - [ ] Extract critical CSS (< 14KB)
  - [ ] Inline critical CSS
  - [ ] Async load non-critical CSS
  - [ ] Test load performance improvement

- [ ] Optimize images
  - [ ] Generate WebP versions
  - [ ] Implement responsive images (srcset)
  - [ ] Add lazy loading
  - [ ] Optimize with Shopify CDN
  - [ ] Measure performance impact

- [ ] Optimize JavaScript
  - [ ] Code split by route/section
  - [ ] Defer non-critical scripts
  - [ ] Remove unused code
  - [ ] Implement tree shaking
  - [ ] Test bundle size reduction

---

## Progress Tracking

### Overall Completion
- 🔴 Immediate Fixes: ⬜⬜⬜⬜⬜ (0/5 days)
- 🟡 Short-Term: ⬜⬜⬜ (0/3 weeks)
- 🟢 Long-Term: ⬜⬜⬜ (0/3 months)

### Quality Metrics Progress

| Metric | Baseline | Target | Current | Status |
|--------|----------|--------|---------|--------|
| Requirements Quality | 3/10 | 8/10 | 3/10 | ⬜ |
| Architecture Clarity | 5/10 | 8/10 | 5/10 | ⬜ |
| Testing Coverage | 2/10 | 9/10 | 2/10 | ⬜ |
| Production Readiness | 4/10 | 9/10 | 4/10 | ⬜ |
| Accessibility | 3/10 | 9/10 | 3/10 | ⬜ |
| Performance | 5/10 | 8/10 | 5/10 | ⬜ |
| **Overall** | **4.5/10** | **8.5/10** | **4.5/10** | ⬜ |

### Lighthouse Scores Progress

| Page | Performance | Accessibility | Best Practices | SEO | Status |
|------|-------------|---------------|----------------|-----|--------|
| Homepage (Desktop) | - | - | - | - | ⬜ |
| Homepage (Mobile) | - | - | - | - | ⬜ |
| Product (Mobile) | - | - | - | - | ⬜ |
| Cart (Mobile) | - | - | - | - | ⬜ |
| Checkout (Mobile) | - | - | - | - | ⬜ |

**Target**: All scores >= 90 (Accessibility >= 95)

---

## Notes & Decisions

### Date: [YYYY-MM-DD]
**Decision**:
**Rationale**:
**Impact**:

### Date: [YYYY-MM-DD]
**Blocker**:
**Resolution**:
**Owner**:

---

## References

- [Full Expert Review](2025-11-11-atlas-theme-review.md)
- [Critical Issues Summary](critical-issues-summary.md)
- [WCAG 2.1 Guidelines](https://www.w3.org/WAI/WCAG21/quickref/)
- [Web Vitals](https://web.dev/vitals/)
- [Shopify Theme Guidelines](https://shopify.dev/themes/best-practices)

---

*Last Updated: November 11, 2025*
