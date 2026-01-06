### **[[01 JWT Fundamentals & Concepts]]**

Master JSON Web Tokens (JWT) as the industry-standard authentication mechanism for modern applications. Learn why JWT is used by Auth0, Okta, and virtually every API-driven company. Understand token-based authentication that replaced session-based auth for stateless, scalable systems. JWT skills are required for all backend and full-stack positions. Essential for API security, microservices, and single sign-on implementations.

|Topic|Focus & Purpose|
|---|---|
|**[[1.1 JWT Introduction]]**|What is JWT; token-based vs session-based auth; stateless authentication; use cases; industry adoption. Core concept.|
|**[[1.2 JWT Structure]]**|Three parts: header, payload, signature; Base64URL encoding; dot separation; anatomy breakdown. Token structure.|
|**[[1.3 Header]]**|Algorithm (alg); token type (typ); key ID (kid); header claims; custom headers. Header section.|
|**[[1.4 Payload (Claims)]]**|Registered claims (iss, sub, exp, iat, aud); public claims; private claims; claim conventions. Payload section.|
|**[[1.5 Signature]]**|Signing algorithms; HMAC; RSA; signature verification; preventing tampering. Security layer.|
|**[[1.6 JWT vs Other Tokens]]**|JWT vs opaque tokens; JWT vs SAML; JWT vs session cookies; comparison; when to use. Token comparison.|
|**[[1.7 JWT Workflow]]**|Authentication flow; token issuance; token validation; request authorization; complete cycle. Auth flow.|

### **[[02 Signing Algorithms]]**

Master JWT signing algorithms for secure token generation. Learn symmetric vs asymmetric algorithms, key management, and algorithm selection. Algorithm knowledge is critical for JWT security.

|Topic|Focus & Purpose|
|---|---|
|**[[2.1 Algorithm Types]]**|Symmetric vs asymmetric; shared secrets vs key pairs; algorithm categories; security levels. Algorithm basics.|
|**[[2.2 HMAC Algorithms]]**|HS256; HS384; HS512; shared secret; when to use HMAC; performance. Symmetric signing.|
|**[[2.3 RSA Algorithms]]**|RS256; RS384; RS512; public/private keys; key generation; RSA benefits. RSA signing.|
|**[[2.4 ECDSA Algorithms]]**|ES256; ES384; ES512; elliptic curves; smaller keys; ECDSA vs RSA. ECDSA signing.|
|**[[2.5 PS Algorithms]]**|PS256; PS384; PS512; RSA-PSS; padding schemes; when to use. PSS signing.|
|**[[2.6 EdDSA Algorithm]]**|Ed25519; modern curves; performance; security; adoption. EdDSA signing.|
|**[[2.7 Algorithm Selection]]**|Choosing algorithms; security requirements; performance; compatibility; best practices. Decision making.|
|**[[2.8 None Algorithm Attack]]**|Algorithm none vulnerability; attack prevention; alg header validation; security. Security vulnerability.|

### **[[03 Token Lifecycle]]**

Master JWT token lifecycle management. Learn token creation, validation, expiration, and renewal. Lifecycle management is essential for secure and user-friendly authentication.

|Topic|Focus & Purpose|
|---|---|
|**[[3.1 Token Creation]]**|Generating tokens; library usage; claim population; signing; issuance time. Token generation.|
|**[[3.2 Token Validation]]**|Signature verification; claim validation; expiration check; audience verification. Token verification.|
|**[[3.3 Expiration (exp)]]**|Setting expiration; short-lived tokens; expiration handling; time drift; clock skew. Token expiry.|
|**[[3.4 Issued At (iat)]]**|Issuance timestamp; token age; replay prevention; iat validation. Issuance time.|
|**[[3.5 Not Before (nbf)]]**|Future activation; delayed tokens; nbf validation; use cases. Activation time.|
|**[[3.6 Token Revocation]]**|Revocation challenges; token blacklisting; Redis blacklist; database tracking; JTI claim. Invalidation.|
|**[[3.7 Token Storage]]**|Client-side storage; localStorage; sessionStorage; cookies; httpOnly; secure flags. Storage options.|
|**[[3.8 Project: Token Manager]]**|Building token lifecycle; creation; validation; expiration; revocation. Lifecycle project.|

### **[[04 Refresh Tokens]]**

Master refresh token patterns for seamless user experience. Learn refresh token implementation, rotation, and security. Refresh tokens enable long sessions while maintaining security.

|Topic|Focus & Purpose|
|---|---|
|**[[4.1 Refresh Token Concept]]**|Why refresh tokens; access vs refresh; token pair pattern; user experience. Refresh basics.|
|**[[4.2 Refresh Token Flow]]**|Token refresh endpoint; exchanging tokens; silent refresh; flow implementation. Refresh flow.|
|**[[4.3 Token Rotation]]**|One-time use refresh tokens; rotation benefits; detecting reuse; security enhancement. Token rotation.|
|**[[4.4 Refresh Token Storage]]**|Database storage; Redis; hashing refresh tokens; secure storage; indexing. Server storage.|
|**[[4.5 Sliding Sessions]]**|Sliding expiration; activity-based renewal; session extension; implementation. Session management.|
|**[[4.6 Family Detection]]**|Token families; reuse detection; family revocation; security breach handling. Breach detection.|
|**[[4.7 Mobile Considerations]]**|Long-lived refresh tokens; biometric re-auth; device binding; mobile patterns. Mobile apps.|
|**[[4.8 Project: Refresh System]]**|Complete refresh implementation; rotation; storage; revocation; security. Refresh project.|

### **[[05 JWT Implementation]]**

Master JWT implementation across different languages and frameworks. Learn popular libraries, best practices, and integration patterns. Implementation skills enable building real-world auth systems.

|Topic|Focus & Purpose|
|---|---|
|**[[5.1 Node.js (jsonwebtoken)]]**|jsonwebtoken library; sign; verify; decode; options; error handling. Node.js JWT.|
|**[[5.2 Node.js (jose)]]**|jose library; modern API; async operations; JWK support; encryption. Modern Node.js.|
|**[[5.3 Python (PyJWT)]]**|PyJWT library; encode; decode; algorithms; options; exceptions. Python JWT.|
|**[[5.4 Python (python-jose)]]**|python-jose; JWK; JWS; JWE; algorithm support; FastAPI integration. Python advanced.|
|**[[5.5 Java (jjwt)]]**|JJWT library; builder pattern; parser; claims; Spring integration. Java JWT.|
|**[[5.6 .NET]]**|System.IdentityModel.Tokens.Jwt; token handlers; ASP.NET Core; claims. .NET JWT.|
|**[[5.7 Go (golang-jwt)]]**|golang-jwt; claims struct; signing; validation; Go patterns. Go JWT.|
|**[[5.8 Project: Multi-Language]]**|Implementing JWT; Node.js; Python; interoperability; testing. Implementation project.|

### **[[06 JWT Security]]**

Master JWT security best practices and vulnerability prevention. Learn common attacks, mitigation strategies, and secure implementation. Security knowledge prevents authentication breaches.

|Topic|Focus & Purpose|
|---|---|
|**[[6.1 Common Vulnerabilities]]**|Algorithm confusion; token injection; weak secrets; information disclosure. Known attacks.|
|**[[6.2 Algorithm Validation]]**|Whitelist algorithms; reject 'none'; strict algorithm checking; prevention. Algorithm security.|
|**[[6.3 Secret Management]]**|Strong secrets; key generation; rotation; storage; environment variables. Key security.|
|**[[6.4 Claim Validation]]**|Validating all claims; audience check; issuer check; custom claim validation. Claim security.|
|**[[6.5 Token Size]]**|Payload size limits; claim minimization; performance impact; storage limits. Size considerations.|
|**[[6.6 Transport Security]]**|HTTPS only; secure cookies; token transmission; man-in-the-middle. Transport security.|
|**[[6.7 XSS & CSRF]]**|XSS token theft; CSRF attacks; cookie vs header; protection strategies. Browser security.|
|**[[6.8 Project: Security Audit]]**|Auditing JWT implementation; fixing vulnerabilities; penetration testing. Security project.|

### **[[07 JWK & Key Management]]**

Master JSON Web Keys (JWK) for key management. Learn JWK format, JWKS endpoints, and key rotation. JWK knowledge is essential for production JWT systems and OAuth integration.

|Topic|Focus & Purpose|
|---|---|
|**[[7.1 JWK Format]]**|JSON Web Key structure; key types (kty); key parameters; key representation. JWK basics.|
|**[[7.2 JWKS (Key Sets)]]**|JWK Set; multiple keys; key selection; keys array; key discovery. Key sets.|
|**[[7.3 JWKS Endpoints]]**|.well-known/jwks.json; public key distribution; endpoint implementation; caching. Key endpoints.|
|**[[7.4 Key ID (kid)]]**|Key identification; kid claim; key lookup; multiple keys; key selection. Key ID usage.|
|**[[7.5 Key Rotation]]**|Rotation strategy; overlap period; graceful rotation; zero downtime. Key rotation.|
|**[[7.6 Key Generation]]**|Generating key pairs; RSA keys; EC keys; key export; secure generation. Creating keys.|
|**[[7.7 Project: JWKS Server]]**|Building JWKS endpoint; key rotation; key caching; production setup. JWK project.|

### **[[08 JWT in Web Applications]]**

Master JWT integration in web applications. Learn frontend storage, API authorization, and SPA patterns. Web application patterns are essential for frontend developers.

|Topic|Focus & Purpose|
|---|---|
|**[[8.1 Frontend Storage]]**|localStorage; sessionStorage; memory; in-memory tokens; storage comparison. Token storage.|
|**[[8.2 HTTP-Only Cookies]]**|Cookie storage; httpOnly flag; secure flag; SameSite; cookie-based JWT. Cookie approach.|
|**[[8.3 Authorization Header]]**|Bearer token; Authorization header; request interceptors; axios/fetch setup. API calls.|
|**[[8.4 Silent Refresh]]**|Background refresh; iframe approach; token expiry handling; seamless UX. Auto refresh.|
|**[[8.5 React Integration]]**|Auth context; protected routes; token management; hooks; state. React patterns.|
|**[[8.6 Vue Integration]]**|Pinia/Vuex; navigation guards; composables; token handling. Vue patterns.|
|**[[8.7 Angular Integration]]**|HTTP interceptors; route guards; services; token management. Angular patterns.|
|**[[8.8 Project: SPA Authentication]]**|Building SPA auth; login; token storage; refresh; protected routes. SPA project.|

### **[[09 JWT in APIs]]**

Master JWT for API authentication and authorization. Learn middleware patterns, permission checking, and API security. API JWT patterns are essential for backend developers.

|Topic|Focus & Purpose|
|---|---|
|**[[9.1 API Authentication Flow]]**|Login endpoint; token response; subsequent requests; stateless auth. API auth flow.|
|**[[9.2 Auth Middleware]]**|JWT middleware; token extraction; validation; error responses; Express/FastAPI. Middleware.|
|**[[9.3 Protected Routes]]**|Route protection; middleware application; public vs private endpoints. Route security.|
|**[[9.4 User Context]]**|Extracting user from token; request context; user injection; claims usage. User identification.|
|**[[9.5 Role-Based Access]]**|Roles in JWT; permission checking; middleware guards; RBAC patterns. Authorization.|
|**[[9.6 API Gateway JWT]]**|Gateway validation; Kong; AWS API Gateway; token verification at edge. Gateway patterns.|
|**[[9.7 Rate Limiting by User]]**|User identification; per-user limits; token-based limiting; abuse prevention. Rate limiting.|
|**[[9.8 Project: Secure API]]**|Building protected API; auth; RBAC; rate limiting; security. API project.|

### **[[10 OAuth 2.0 & JWT]]**

Master JWT with OAuth 2.0 for industry-standard authentication. Learn OAuth flows with JWT, OIDC, and third-party integration. OAuth+JWT is the standard for modern authentication.

|Topic|Focus & Purpose|
|---|---|
|**[[10.1 OAuth 2.0 Overview]]**|OAuth concepts; authorization vs authentication; flows; grant types. OAuth basics.|
|**[[10.2 Access Tokens as JWT]]**|JWT access tokens; self-contained tokens; validation; claim mapping. JWT access tokens.|
|**[[10.3 ID Tokens (OIDC)]]**|OpenID Connect; ID token claims; user info; authentication proof. OIDC tokens.|
|**[[10.4 Authorization Code Flow]]**|Code flow; PKCE; token exchange; JWT response; secure flow. Auth code flow.|
|**[[10.5 Client Credentials]]**|Machine-to-machine; service accounts; JWT grant; scope-based access. M2M auth.|
|**[[10.6 Token Introspection]]**|Introspection endpoint; token validation; active status; claim retrieval. Token verification.|
|**[[10.7 Third-Party Providers]]**|Auth0; Okta; Cognito; Firebase Auth; provider integration. Auth providers.|
|**[[10.8 Project: OAuth Implementation]]**|Building OAuth server; JWT tokens; flows; OIDC; integration. OAuth project.|

### **[[11 Microservices & JWT]]**

Master JWT in microservices architectures. Learn service-to-service auth, token propagation, and distributed systems. Microservices JWT is essential for modern backend architectures.

|Topic|Focus & Purpose|
|---|---|
|**[[11.1 Service Authentication]]**|Service identity; service tokens; mutual TLS vs JWT; trust boundaries. Service auth.|
|**[[11.2 Token Propagation]]**|Passing tokens between services; request context; token forwarding. Token passing.|
|**[[11.3 Token Exchange]]**|RFC 8693; token exchange; audience restriction; scope reduction. Token exchange.|
|**[[11.4 API Gateway Auth]]**|Gateway JWT validation; downstream propagation; token transformation. Gateway patterns.|
|**[[11.5 Sidecar Proxies]]**|Envoy; Istio; JWT validation at proxy; service mesh auth. Service mesh.|
|**[[11.6 Centralized Auth Service]]**|Dedicated auth service; token issuance; validation service; architecture. Auth service.|
|**[[11.7 Claims Enrichment]]**|Adding claims; user data; permissions; enrichment middleware. Claim enhancement.|
|**[[11.8 Project: Microservices Auth]]**|Building distributed auth; gateway; services; token flow; security. Microservices project.|

### **[[12 JWE (Encryption)]]**

Master JSON Web Encryption for confidential tokens. Learn encrypted JWT, encryption algorithms, and when to encrypt. JWE protects sensitive claim data from exposure.

|Topic|Focus & Purpose|
|---|---|
|**[[12.1 JWE Introduction]]**|What is JWE; signed vs encrypted; when to encrypt; use cases. Encryption basics.|
|**[[12.2 JWE Structure]]**|Five parts; protected header; encrypted key; IV; ciphertext; tag. JWE anatomy.|
|**[[12.3 Encryption Algorithms]]**|A256GCM; A128CBC-HS256; content encryption; algorithm selection. Encryption algs.|
|**[[12.4 Key Encryption]]**|RSA-OAEP; ECDH-ES; direct encryption; key wrapping; key agreement. Key encryption.|
|**[[12.5 Nested JWT]]**|Sign-then-encrypt; encrypt-then-sign; nesting patterns; security. Nested tokens.|
|**[[12.6 JWE Implementation]]**|Library support; jose; encryption/decryption code; key management. Implementation.|
|**[[12.7 Project: Encrypted Tokens]]**|Building JWE system; sensitive claims; encryption; decryption. JWE project.|

### **[[13 Testing & Debugging]]**

Master JWT testing and debugging techniques. Learn testing strategies, debugging tools, and troubleshooting. Testing skills ensure reliable authentication systems.

|Topic|Focus & Purpose|
|---|---|
|**[[13.1 JWT Debugging Tools]]**|jwt.io; token inspection; claim viewing; signature verification testing. Debug tools.|
|**[[13.2 Unit Testing]]**|Testing token generation; mocking; claim assertions; algorithm tests. Unit tests.|
|**[[13.3 Integration Testing]]**|Auth flow testing; protected endpoint tests; token lifecycle tests. Integration tests.|
|**[[13.4 Mock Tokens]]**|Test token generation; fixture tokens; deterministic tokens; test utilities. Test doubles.|
|**[[13.5 Time-Based Testing]]**|Mocking time; expiration testing; clock manipulation; edge cases. Time testing.|
|**[[13.6 Security Testing]]**|Algorithm attacks; signature bypass; claim manipulation; penetration. Security tests.|
|**[[13.7 Project: Test Suite]]**|Complete JWT testing; unit; integration; security; coverage. Testing project.|

### **[[14 Production Patterns]]**

Master production-ready JWT implementations. Learn scalability, monitoring, and enterprise patterns. Production patterns are essential for real-world systems.

|Topic|Focus & Purpose|
|---|---|
|**[[14.1 Scalability]]**|Stateless benefits; horizontal scaling; no session storage; load balancing. Scale patterns.|
|**[[14.2 Performance]]**|Validation caching; JWKS caching; algorithm performance; optimization. Performance.|
|**[[14.3 Logging & Monitoring]]**|Auth event logging; failed attempts; token metrics; alerting. Observability.|
|**[[14.4 Error Handling]]**|Token errors; user-friendly messages; error codes; retry guidance. Error handling.|
|**[[14.5 Versioning]]**|Token versioning; claim migration; backward compatibility; upgrades. Version management.|
|**[[14.6 Disaster Recovery]]**|Key compromise; mass revocation; emergency rotation; incident response. Recovery.|
|**[[14.7 Compliance]]**|GDPR; claim minimization; data protection; audit trails; privacy. Compliance.|
|**[[14.8 Project: Production Auth]]**|Building production system; monitoring; security; scale; reliability. Production project.|
