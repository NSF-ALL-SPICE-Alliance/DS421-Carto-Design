# Deploying a Shiny App to Posit Connect Cloud (via GitHub)

## Prerequisites
- The code to generate your shiny app is in a .R script called `app.R` 
- A **DS421-Carto-Design Repository** with your latest changes pushed.

## Steps

1. **Create a Posit Connect Cloud account.** [sign up for free account here](https://connect.posit.cloud/)
2. **Sign up with GitHub** and **authorize** access.
3. **Create your account name** (recommended: first + last name, no spaces).
4. **Skip** the optional profile form.
5. In Connect Cloud, click **Publish**.
6. **Install the GitHub App** for Connect Cloud and complete **authentication**.
7. Select the **Shiny** framework.
8. Ensure the app you want to publish is an R script named **`app.R`** and that the **most recent version is pushed to GitHub**.
9. Generate a deployment manifest with **rsconnect**:
   ```r
   rsconnect::writeManifest()
   ```
10. **Commit and push** the new **`manifest.json`** file to GitHub.
11. **Commit and push your data files** (CSV, GeoJSON, **all** Shapefile components, `.gpkg`, etc.). Use **relative paths** in your app code (e.g., `here::here("data", "file.csv")`).
12. In Connect Cloud, choose your repository (e.g., **DS421-Carto-Design**).
13. Select the **main** branch.
14. Set **Primary file** to **`app.R`**.
15. (Optional) Enable **Automatically publish on push**.
16. Click **Publish**.

## Build & Logs
- Watch **status updates** and **build logs** during deployment.
- On success, you’ll get a **shareable URL**.

## Submission Checklist
- [ ] Repo contains `app.R` at the root.
- [ ] `manifest.json` created with `rsconnect::writeManifest()` and pushed.
- [ ] Data files pushed (CSV/GeoJSON/**all** Shapefile parts, or `.gpkg`, etc.).
- [ ] Repo: `DS421-Carto-Design`, Branch: `main`, Primary file: `app.R`.
- [ ] (Optional) Auto-publish on push enabled.
- [ ] App published; URL verified.
