# Web Developer Log

<div align="center">
    <img src="./assets/site-header.png" alt="Web Developer Log Header" width="80%" />
</div>

## NOTICE

This website is currently under maintenance due to issues with the X API. Will be back up within the week. - 8/23/25

## Description

This project was created in effort to practice creating a full stack web application using a 
well-established third party API from a popular platform. It has also been a useful way to use 
a MERN stack application to practice working around a third party API in conjunction with a 
MongoDB database. By using the Twitter platform as a design model for this application, I was able to 
replicate many of the important features of a social media feed, while being sure to design mobile-first.

IMPORTANT: Since Twitter was bought and changed to X, this application no longer functions correctly 
due to X making their API services no longer free. I have plans to manually input the profile's feed 
data into the database so that the website can still show previous activity, but currently the hosted 
site does not work.

## Table of Contents

* [Description](#description)
* [Preview](#preview)
* [Development](#development)
* [Installation](#installation)
* [Usage](#usage)
* [Contributing](#contributing)
* [Credits](#credits)
* [License](#license)

## Preview

<div align="center">
    <img src="./assets/site-preview.png" alt="Site Preview" width="100%" />
</div>

## Development

This code example is used to show how the main parent component asynchronously pulls data from the 
back-end internal API and passes it on to the child components. Visually, the app emulates the classic 
Twitter feed by styling first for the smallest viewport sizes taking advantage of Bootstrap's breakpoint 
classes.

```js
class App extends Component {
    constructor(props) {
        super(props);
        this.state = {
            tweets: [],
            news: []
        }
    }

    componentDidMount = async () => {
        const response = await API.updateTweets();
        console.log(response);

        const tweets = await API.getTweets();
        const listTweets = await API.getListTweets();
        this.setState({ tweets: tweets.data, news: listTweets.data });
    }

    render() {
        return (
            <Container fluid="xxl" className="px-0 h-100">
                <Row className="g-0 vh-100">
                    <Col sm={2} className="border-end border-white border-3...">
                        <LeftPanel />
                    </Col>
                    <Col xs={12} sm={10} md={6} className="h-100 overflow-auto">
                        <Feed tweets={this.state.tweets} />
                    </Col>
                    <Col md={4} className="border-start border-white border-3...">
                        <RightPanel news={this.state.news} />
                    </Col>
                </Row>
            </Container>
        );
    }
}
```

## Installation

To install the required npm packages to run this application, clone the repository and run the following command:
```sh
npm install
```

## Usage

To use this application, run the following command:
```sh
npm start
```

## Contributing

<div>
    <img src="./assets/profile-picture-circle.png" alt="Simon Newton Profile Picture" width=250 />
    <h3><b>Simon Newton</b></h3>
    <hr align=left width=350 />
    <p>Full-Stack Web Developer!</p>
    <a href="https://github.com/simonanewton" target="_blank">GitHub Profile</a> | <a href="https://www.linkedin.com/in/simonanewtondev/" target="_blank">LinkedIn Profile</a> | <a href="https://developer-portfolio-yqdu.onrender.com/" target="_blank">Personal Website</a>
</div>

## Credits

External API Reference
* https://developer.twitter.com/en/docs/twitter-api

Development Resources
* https://fontawesome.com/
* https://reactjs.org/
* https://react-bootstrap.github.io/

Primary NPM Packages
* https://npmjs.com/package/react
* https://npmjs.com/package/react-bootstrap
* https://npmjs.com/package/mongoose
* https://npmjs.com/package/express

## License

[![license](https://img.shields.io/badge/license-MIT-green)](https://simonanewton.mit-license.org)

MIT License &copy; Simon Newton <https://simonanewton.mit-license.org>
