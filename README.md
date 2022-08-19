# microfrontend
A basic micro front end app using Module Federation of Webpack

## webpack.config

{
	mode:development,
	devServer: {port: 8081},
	plugins: [
		new ModuleFederationPlugin(
			{
				name:
				filename:
				exposes:
				shared: ['faker']
				shared: { faker: {singleton: true}}
			}
			{
				name:
				remotes:
			}
		)
		new HTMLWebpackPlugin(
			{
				template: 'public/index.js'
			}
		)
	]
	
}

## Points to remember

* Difference between webpack and webpack serve
* Designate one app as the Host and one as the Remote
* In the Remote, decide which modules(files) you want to make available to other
* Set up Module Federation to expose those files
* In the host, decide which files you want to get from the remote
* Set up Module Federation to expose those files
* In the host, refactor the entry point to load asynchronosly (import ('./bootstrap.js'))
* In the host, import whatever files you want to from the remote

* Shared When run in isolation, shared modules are loaded asynchronosly which might cause the error 'shared module is not available for eager consumption'
import(./bootstrap) is the solution

* ^carrot version in front of node modules, which tell to ignore the sub versions in Sharing.
~version, things are different
* When loading 2 entirely different versions and singleton:true. Conflicts arise asking to choose one option

* webpack will automatically replace process.env.NODE_ENV to development if mode === 'development'

* Bug Alert: dont use the div ids same as the remote project name

* npm install webpack@5.68.0 webpack-cli@4.10.0 webpack-dev-server@4.7.4 html-webpack-plugin@5.5.0 nodemon