# echizencity-hazardmap

> 日本語のREADMEはこちらです: [README.ja.md](README.ja.md)

This project uses data from [Echizen City Open Data](https://www.city.echizen.lg.jp/office/010/021/open-data-echizen.html), including evacuation centers, AEDs, and medical institutions.

## Municipal Hazard Map Template

This project uses the "Municipal Hazard Map Template" ([shikuchoson-hazardmap-template](https://github.com/sankichi92/shikuchoson-hazardmap-template)) to create web-based municipal hazard maps.

This is the result of [Tokyo OSS Party!!](https://tokyo-oss-party.com/) 2021. The presentation slides are available at https://speakerdeck.com/sankichi92/shikuchoson-hazardmap-template

## Example Usage

- [Hachioji City](https://sankichi.net/hachioji-hazardmap/) ([sankichi92/hachioji-hazardmap](https://github.com/sankichi92/hachioji-hazardmap))

## Background and Challenges

Hazard maps in Japan are compiled on the [Hazard Map Portal Site](https://disaportal.gsi.go.jp/) managed by the Ministry of Land, Infrastructure, Transport and Tourism, which provides the following two services:

- Overlaying Hazard Maps: A web map service that allows you to overlay disaster risk information and other useful disaster prevention information nationwide.
- Finding Municipal Hazard Maps: A link collection of hazard maps created by municipalities.

The "Overlaying Hazard Maps" is a well-designed and highly functional web map, but as stated in [the usage guide](https://disaportal.gsi.go.jp/hazardmap/pamphlet/pamphlet.html):

> For detailed information, please refer to the hazard maps created by the municipalities.

In other words, it is a national map, and the details of each municipality cannot be confirmed.

What is often required of hazard maps is not broad, shallow information about the country as a whole, but narrow, deep information about the specific location where one lives. To confirm such information, it is necessary to check the hazard maps of the municipalities through the "Finding Municipal Hazard Maps".

However, many of the hazard maps created by municipalities are premised on paper distribution, and are not optimized for the web, unlike the "Overlaying Hazard Maps". And probably, there are not many municipalities that have the budget and resources to develop and operate their own web-based hazard maps.

To address this issue, this project provides a template that allows municipalities to easily create and customize web-based hazard maps.

## Usage

Watch the video: https://youtu.be/oc1CfaVSlno

### Creating and Publishing Hazard Maps

#### 1. Create a GitHub repository using the template

1. Click the "Use this template" button at the top (or here)
2. Enter a Repository name (e.g. `hachioji-hazardmap`) and click "Create repository from template"
   - The Repository name will be part of the URL of the web page you publish in the next step

Details: https://docs.github.com/en/repositories/creating-and-managing-repositories/creating-a-repository-from-a-template

#### 2. Update the `hazardmap-config.jsonc` file for the target municipality

1. Click on the [`hazardmap-config.jsonc`](./hazardmap-config.jsonc) file in the created repository to open it
2. Click the pencil ✏️ button in the top right to enter the edit mode
3. Change the values of `prefecture` and `city` to the prefecture and municipality for which you are creating the hazard map, and click the "Commit changes" button
   - Also, delete any unnecessary `tiles` elements (`{}` enclosed units). For example, if it's an inland area, "High tide inundation area" may not be necessary.

Details: https://docs.github.com/en/repositories/working-with-files/managing-files/editing-files#editing-files-in-your-repository

#### 3. Enable GitHub Pages in the settings of the created repository to publish the web page

1. Go to the Settings tab > Pages sidebar to access the GitHub Pages settings
2. Select "`gh-pages`" as the Source and click the "Save" button
3. After a while, a URL will be displayed on the GitHub Pages settings page, and the hazard map will be published at that URL.

Details: https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site

### Customizing the Hazard Map

#### Adding custom layers by uploading CSV files

1. Click on the [`csv`](./csv) folder in the created repository to view its contents
2. Click "Add files" > "Upload files" to upload a CSV file, then click the "Commit changes" button
3. View [`01-サンプル.csv`](./csv/01-サンプル.csv) and click the trash can 🗑 button in the top right to delete the file

Details: https://docs.github.com/en/repositories/working-with-files/managing-files/adding-a-file-to-a-repository

##### About the CSV format

The CSV file must have the `name`, `lat` (latitude), and `lon` (longitude) columns.
Additionally, other columns can be added, and they will be displayed when the map icon is clicked.
The file name prefix `01-` is used to determine the display order on the map, but the number itself is not displayed on the map.

Please refer to [`01-サンプル.csv`](./csv/01-サンプル.csv) as an example.

#### Uploading images to display in the bottom left of the map

Similar to CSV, you can upload images to the [`images`](./images) directory, and they will be displayed in the bottom left of the map.

## Development

This project was created using [Create React App](https://github.com/facebook/create-react-app).

The following commands are available:

### `npm start`

Runs the app in the development mode.\
Open [http://localhost:3000](http://localhost:3000) to view it in the browser.

The page will reload if you make edits.\
You will also see any lint errors in the console.

### `npm run build`

Builds the app for production to the `build` folder.

### `npm run prebuild`

Updates the files under `src/generated` based on the contents of `hazardmap-config.jsonc`, `csv`, and `images` directories.\
You need to run this command before `npm start` to reflect changes in the aforementioned files and directories.

### `npm run format`

Formats the code under `src` using [Prettier](https://prettier.io/).

MIT License — see [LICENSE](LICENSE).