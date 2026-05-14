# echizencity-hazardmap

> 日本語のREADMEはこちらです: [README.ja.md](README.ja.md)

This repository contains the source code for the [Echizen City Hazard Map](https://code4fukui.github.io/echizencity-hazardmap/), a web-based hazard map that visualizes disaster risks and safety information for Echizen City, Fukui Prefecture.

It utilizes open data from [Echizen City Open Data](https://www.city.echizen.lg.jp/office/010/021/open-data-echizen.html), including evacuation centers, AED locations, and medical institutions.


![Echizen City Hazard Map Screenshot](https://raw.githubusercontent.com/sankichi92/shikuchoson-hazardmap-template/main/docs/screenshot.png)


## About the Template

This project is an implementation of the **[Municipal Hazard Map Template](https://github.com/sankichi92/shikuchoson-hazardmap-template)**, designed to help municipalities easily create and publish their own web-based hazard maps.

The template was created as a result of [Tokyo OSS Party!! 2021](https://tokyo-oss-party.com/).
- **Presentation Slides:** [speakerdeck.com/sankichi92/shikuchoson-hazardmap-template](https://speakerdeck.com/sankichi92/shikuchoson-hazardmap-template)
- **Template Usage Example:** [Hachioji City Hazard Map](https://sankichi.net/hachioji-hazardmap/) ([GitHub Repo](https://github.com/sankichi92/hachioji-hazardmap))

## Background

In Japan, hazard maps are aggregated on the [Hazard Map Portal Site](https://disaportal.gsi.go.jp/) managed by the Ministry of Land, Infrastructure, Transport and Tourism. While the portal's "Overlaying Hazard Maps" service is a powerful national tool, it lacks the detailed, local information residents need. The portal itself advises users to "refer to the hazard maps created by the municipalities for detailed information."

However, many municipal hazard maps are designed for paper distribution and are not optimized for the web. Municipalities often lack the budget and resources to develop and operate their own interactive web maps. This template provides a solution by enabling the easy creation and customization of web-based hazard maps using a standardized, open-source framework.

## How to Create Your Own Hazard Map

You can create a hazard map for any municipality by following these steps.

Watch the video tutorial: [https://youtu.be/oc1CfaVSlno](https://youtu.be/oc1CfaVSlno)

#### 1. Create a Repository from the Template

1.  Navigate to the [template repository](https://github.com/sankichi92/shikuchoson-hazardmap-template).
2.  Click the **"Use this template"** button.
3.  Enter a repository name (e.g., `mycity-hazardmap`) and click **"Create repository from template"**.

(See GitHub Docs: [Creating a repository from a template](https://docs.github.com/en/repositories/creating-and-managing-repositories/creating-a-repository-from-a-template))

#### 2. Configure for Your Municipality

1.  In your new repository, open the `hazardmap-config.jsonc` file.
2.  Click the pencil icon (✏️) to edit the file.
3.  Change the `prefecture` and `city` values to your target municipality.
4.  Remove any unnecessary hazard layers from the `tiles` array (e.g., "High tide inundation area" for an inland city).
5.  Click **"Commit changes"**.

(See GitHub Docs: [Editing files in your repository](https://docs.github.com/en/repositories/working-with-files/managing-files/editing-files#editing-files-in-your-repository))

#### 3. Publish with GitHub Pages

1.  Go to your repository's **Settings** tab and select **Pages** from the sidebar.
2.  Under **Source**, select the `gh-pages` branch.
3.  Click **"Save"**.
4.  After a few minutes, your hazard map will be published at the URL displayed on the page. The build and deployment process is handled automatically by a GitHub Action.

(See GitHub Docs: [Configuring a publishing source for your GitHub Pages site](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site))

## Customization

#### Adding Custom Data Layers (CSV)

1.  Navigate to the `csv` folder in your repository.
2.  Click **"Add file"** > **"Upload files"** to add your own CSV data.
3.  The CSV file must contain `name`, `lat` (latitude), and `lon` (longitude) columns. Any additional columns will be displayed in the popup when a map icon is clicked.
4.  The filename prefix (e.g., `01-`) determines the display order in the layer control.

(See GitHub Docs: [Adding a file to a repository](https://docs.github.com/en/repositories/working-with-files/managing-files/adding-a-file-to-a-repository))

#### Adding Custom Legend Images

1.  Navigate to the `images` folder.
2.  Upload your legend images (e.g., PNG, JPG). They will be automatically displayed in the bottom-left corner of the map.

## Development

This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app). To run the project locally:

1.  Clone the repository.
2.  Install dependencies: `npm install`
3.  Run the pre-build script to process configuration and data: `npm run prebuild`
4.  Start the development server: `npm start`

### Available Scripts

-   **`npm start`**: Runs the app in development mode at [http://localhost:3000](http://localhost:3000).
-   **`npm run build`**: Builds the app for production to the `build` folder.
-   **`npm run prebuild`**: Processes `hazardmap-config.jsonc`, `csv`, and `images` files into a format the application can use. You must run this before `npm start` if you change these files.
-   **`npm run format`**: Formats code using [Prettier](https://prettier.io/).

## License

This project is available under the [MIT License](LICENSE).