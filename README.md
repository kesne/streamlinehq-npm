# NPM package for Streamline icons and illustrations
This is a small library which downloads Streamline assets you have access to into your local folder so that they can be used in your Javascript project.

It uses a local config file which contains your unique `secret` - an npm token - which should be taken from your [Streamline npm package page](https://app.streamlinehq.com/profile/developer).

The config file must be kept away from code repository as it contains your secret token. Please keep it safe.

Check an example app in the `docs` folder to see how would you use this package.

## How to use
1. Ensure that you have an active Streamline subscription.
2. Add a line `streamlinehq.json` to your project's `.gitignore` file to remove the config from your repository.
3. (optional) Create an example config file and put it in your repo so that your team members can quickly create their own copy for development. Feel free to copy an example file from `docs/streamline_example.json` and feel it with a random secret token. 
4. Copy/paste a config file from `docs/example-app/streamlinehq_example.json` into your project root folder and rename it to `streamlinehq.json`. Make sure it's not added to git.
5. Edit its contents with:   
    - `families`: an array of strings with names of Streamline icons or illustrations families you own and which you want to include in your project. You can take the name from its url in Streamline. Eg a name of Brooklyn Illustrations from page https://app.streamlinehq.com/illustrations-brooklyn is `illustrations-brooklyn`.
    - `secret`: your private npm token which is taken from [Streamline developer page](https://app.streamlinehq.com/profile/developer)
6. Finally, install the package in your project with npm or yarn `yarn add @streamlinehq/streamlinehq`.

It will execute the `postinstall` script which will fetch the graphical assets. The requested images in a form of SVG files will be put in the package's `images` folder. After this you will be able to import those images as usual in your project, eg:
```jsx
// This is just an svg file. You can then use it in your <img> tag.
import checkCircle1 from '@streamlinehq/streamlinehq/images/streamline-bold/check-circle-1.svg'
```

## How to change style, size, etc
Streamline images are just svg files. As a rule of thumb you should either render them as images and change the styles of the `<img>` tag, either inline render them as svg and change styles with css. Check out an example app's code to see more options.

## Troubleshooting
In 95% of the cases you need to ensure that you have a proper `streamlinehq.json` file in your project and reinstall node packages by removing them completely and then installing them again.

Note that because of fetching images installation might take longer than usual.

Double check that images have been installed in your `node_modules/@streamlinehq/streamlinehq/images` folder. If not - try reinstalling on a better internet connection.

If that didn't help or if you have any questions please open an issue.

## Notes

- It has 0 dependencies.
- It works with typescript just fine as it just serves svg image files.
