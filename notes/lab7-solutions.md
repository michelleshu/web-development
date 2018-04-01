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
            players: [],
            teams: {}
        };

        this.addToPlayers = this.addToPlayers.bind(this);
    }

    addToPlayers(player) {
        const newPlayers = this.state.players.concat(player);
        this.setState({
            players: newPlayers
        });

        // Update teams as well
        this.updateTeams(player);
    }

    updateTeams(newPlayer) {
        const teams = Object.assign({}, this.state.teams);
        const newPlayerTeamName = newPlayer.team;
        const team = Object.assign({}, teams[newPlayerTeamName]);
        
        if (!team.name) {
            team.name = newPlayerTeamName;
        }
    
        if (!team.score) {
            team.score = 0;
        }
        team.score += parseInt(newPlayer.score);
    
        teams[newPlayerTeamName] = team;
        this.setState({ teams: teams });
    }

    render() {
        return (
            <div className="container">
                <div className="jumbotron bg-info text-white text-center">
                    <h1>Laser Tag Leaderboard</h1>
                </div>
                <IndividualLeaderboard players={this.state.players} />
                <TeamLeaderboard teams={this.state.teams} />
                <AddPlayer addToPlayers={this.addToPlayers} />
            </div>
        );
    }
}

export default Main;
```

TeamLeaderboard.js
```js
import React from 'react';

class TeamLeaderboard extends React.Component {
    render() {
        return (
            <div className="team-leaderboard">
                <h3>Team Leaderboard</h3>
                <table className="table">
                    <thead>
                        <tr>
                            <th scope="col">Rank</th>
                            <th scope="col">Team</th>
                            <th scope="col">Score</th>
                        </tr>
                    </thead>
                    <tbody>
                        {Object.keys(this.props.teams)
                            .map((teamName) => this.props.teams[teamName])
                            .sort((teamA, teamB) => {
                                return parseInt(teamA.score) < parseInt(teamB.score);
                            })
                            .map((team, index) => {
                                return (                        
                                    <tr key={index}>
                                        <th scope="row">{index + 1}</th>
                                        <td>{team.name}</td>
                                        <td>{team.score}</td>
                                    </tr>
                                );
                        })}
                    </tbody>
                </table>
            </div>
        )
    }
}

export default TeamLeaderboard;
```

IndividualLeaderboard.js (no change since lab 6)
```js
import React from 'react';

class IndividualLeaderboard extends React.Component {
    render() {
        return (
            <div className="individual-leaderboard">
                <h3>Individual Leaderboard</h3>
                <table className="table">
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