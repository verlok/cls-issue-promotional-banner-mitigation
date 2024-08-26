# Mitigation of a CLS issue due to promotional banners injected on the page

To address the CLS (Cumulative Layout Shift) issue caused by the promotional banner, you can implement a solution that saves the promotional content to `sessionStorage` the first time it's rendered. 

Then, on subsequent page loads, the content is read from `sessionStorage` and injected into the page if it exists. 

Additionally, you need to ensure that if the user closes the banner, it is not rendered again during the session.

See the demo in the single HTML file `index.html`.

### Explanation:

1. **Checking if Banner is Closed:** Before anything is done, the script checks if the banner was previously closed by the user. If so, the banner won't be shown again during the session.

2. **Injecting Banner Content:** If the banner has not been closed and there is saved content in `sessionStorage`, it is injected into the designated banner container (`#promo-banner`) and displayed.

3. **Saving Banner Content:** When the promotional content is fetched for the first time (simulated here by clicking a "Fetch Promo" button), the content is saved to `sessionStorage`, so it can be reused on subsequent page loads.

4. **Handling Banner Closure:** If the user closes the banner, a flag (`promoBannerClosed`) is set in `sessionStorage` to prevent the banner from being shown again during the session.

### Notes:

- **`sessionStorage`** is used so that the data persists only for the duration of the user's session, ensuring a fresh start on a new session.
- **The `injectBanner` function** is responsible for displaying the saved content.
- **The `closeBanner` function** hides the banner and prevents it from being shown again in the same session.

Replace the placeholder content and IDs with your actual content and structure as needed.