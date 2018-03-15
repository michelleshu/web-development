Main.js
```js
import React from 'react';
import IndividualLeaderboard from './IndividualLeaderboard';
import TeamLeaderboard from './TeamLeaderboard';
import AddPlayer from './AddPlayer';

class Main extends React.Component {
    constructor(props) {
        super(props);

        this.state = {
            players: []
        };

        this.addToPlayers = this.addToPlayers.bind(this);
    }

    addToPlayers(player) {
        const newPlayers = this.state.players.concat(player);
        this.setState({
            players: newPlayers
        });
    }

    render() {
        return (
            <div className="container">
                <div className="jumbotron bg-info text-white text-center">
                    <h1>Laser Tag Leaderboard</h1>
                </div>
                <IndividualLeaderboard players={this.state.players}/>
                <TeamLeaderboard />
                <AddPlayer addToPlayers={this.addToPlayers} />
            </div>
        );
    }
}

export default Main;
```

AddPlayer.js
```js
import React from 'react';

class AddPlayer extends React.Component {
    constructor(props) {
        super(props);

        this.state = {
            firstName: '',
            lastName: '',
            score: '',
            accuracy: '',
            team: 'Blue'
        };

        this.handleChange = this.handleChange.bind(this);
        this.handleSubmit = this.handleSubmit.bind(this);
    }

    handleSubmit(event) {
        event.preventDefault(); // prevent page from refreshing
        this.props.addToPlayers(this.state);

        this.setState({
            firstName: '',
            lastName: '',
            score: '',
            accuracy: '',
            team: 'Blue'
        });
    }

    handleChange(event) {
        const inputName = event.target.name;
        const inputValue = event.target.value;

        const state = {};
        state[inputName] = inputValue;
        this.setState(state);

        // shorthand:
        // this.setState({
        //    [inputName]: inputValue
        // });
    }

    render() {
        return (
            <div className="add-player-form">
                <h3>Add Player</h3>
                <form onSubmit={this.handleSubmit}>
                    <div className="form-group">
                        <label htmlFor="first-name">First Name</label>
                        <input type="text" id="first-name" value={this.state.firstName} onChange={this.handleChange} name="firstName" className="form-control" placeholder="First Name" />
                    </div>
                    <div className="form-group">
                        <label htmlFor="last-name">Last Name</label>
                        <input type="text" id="last-name" value={this.state.lastName} onChange={this.handleChange} name="lastName" className="form-control" placeholder="Last Name" />
                    </div>
                    <div className="form-group">
                        <label htmlFor="last-name">Score</label>
                        <input type="text" id="score" value={this.state.score} name="score" onChange={this.handleChange} className="form-control" placeholder="0" />
                    </div>
                    <div className="form-group">
                        <label htmlFor="accuracy">Accuracy</label>
                        <input type="text" id="accuracy" value={this.state.accuracy} name="accuracy" onChange={this.handleChange} className="form-control" placeholder="0%" />
                    </div>
                    <div className="form-group">
                        <label htmlFor="team">Team</label>
                        <select className="form-control" value={this.state.team} name="team" onChange={this.handleChange} id="team">
                            <option value="Blue">Blue</option>
                            <option value="Green">Green</option>
                            <option value="Red">Red</option>
                        </select>
                    </div>
                    <div className="button-row">
                        <button className="btn btn-default btn-info" type="submit">Add</button>
                    </div>
                </form>
            </div>
        );
    }
}

export default AddPlayer;
```

IndividualLeaderboard.js
```js
import React from 'react';

class IndividualLeaderboard extends React.Component {
    render() {
        return (
            <div class="individual-leaderboard">
                <h3>Individual Leaderboard</h3>
                <table class="table">
                    <thead>
                        <tr>
                            <th scope="col">Rank</th>
                            <th scope="col">First Name</th>
                            <th scope="col">Last Name</th>
                            <th scope="col">Score</th>
                            <th scope="col">Accuracy</th>
                            <th scope="col">Team</th>
                        </tr>
                    </thead>
                    <tbody>
                        {this.props.players
                            .sort((playerA, playerB) => {
                                return parseInt(playerA.score) < parseInt(playerB.score);
                            })
                            .map((player, index) => {
                            return (
                                <tr key={index}>
                                    <th scope="row">{index + 1}</th>
                                    <td>{player.firstName}</td>
                                    <td>{player.lastName}</td>
                                    <td>{player.score}</td>
                                    <td>{player.accuracy}</td>
                                    <td>{player.team}</td>
                                </tr>
                            );
                        })}
                    </tbody>
                </table>
            </div>
        )
    }
}

export default IndividualLeaderboard;
```
