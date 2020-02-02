<template>
  <div class="container">    

    <div class="bracket">

      <!-- RIGHT SIDE C - D -->
      <div class="bracket__right">

        <div class="bracket__right-matches">
          
          <div class="bracket__right-top">

            <div class="bracket__right-top-teams">


              <div v-for="(game,index) in bracketData.groups[2].games" v-bind:key="index" class="bracket__col">
                <div class="bracket__teams">

                  <p class="bracket__team">
                    <span class="bracket__team-title">{{game.team1.name}}</span>
                    <span class="bracket__teamLogo">
                      {{game.team1.nodeNumber}} <TeamIcon :need="game.team1.name.toLowerCase()"/>
                    </span>                    
                    <span class="line"></span>
                  </p>
                  <p class="bracket__team">
                    <span class="bracket__team-title">{{game.team2.name}}</span>
                    <span class="bracket__teamLogo">
                      {{game.team2.nodeNumber}} <TeamIcon :need="game.team2.name.toLowerCase()"/>
                    </span>                    
                    <span class="line"></span>                              
                  </p>
                </div>

                <div class="bracket__colResult bracket__colResult-inner">                  
                  <select v-model="roundOf16[game.matchId].gameWinner">
                    <option :value="`${game.team1.name}`">{{game.team1.name}}</option>
                    <option :value="`${game.team2.name}`">{{game.team2.name}}</option>
                  </select>
                  <span class="line"></span>
                </div>
              </div>

            </div>

            <div class="bracket__right-top-result">
              <div class="bracket__right-top-result-inner">
                <select v-model="quarterFinals.game3Winner">

                  <option 
                    v-for="(team,index) in gorupCpossibilities"
                    v-bind:key="index"
                  >{{team.name}}</option>
                  
                </select>
                <span class="line"></span>
              </div>
            </div>

          </div>


          <div class="bracket__right-bottom">

            <div class="bracket__right-top-teams">

              <div v-for="(game,index) in bracketData.groups[3].games" v-bind:key="index" class="bracket__col">
                <div class="bracket__teams">

                  <p class="bracket__team">
                    <span class="bracket__team-title">{{game.team1.name}}</span>
                    <span class="bracket__teamLogo">
                      {{game.team1.nodeNumber}} <TeamIcon :need="game.team1.name.toLowerCase()"/>
                    </span>                    
                    <span class="line"></span>
                  </p>
                  <p class="bracket__team">
                    <span class="bracket__team-title">{{game.team2.name}}</span>
                    <span class="bracket__teamLogo">
                      {{game.team2.nodeNumber}} <TeamIcon :need="game.team2.name.toLowerCase()"/>
                    </span>                    
                    <span class="line"></span>                              
                  </p>
                </div>

                <div class="bracket__colResult bracket__colResult-inner">                  
                  <select v-model="roundOf16[game.matchId].gameWinner">
                    <option :value="`${game.team1.name}`">{{game.team1.name}}</option>
                    <option :value="`${game.team2.name}`">{{game.team2.name}}</option>
                  </select>
                  <span class="line"></span>
                </div>
              </div>

            </div>

            <div class="bracket__right-top-result">
              
              <div class="bracket__right-top-result-inner">
                <select v-model="quarterFinals.game4Winner">
                  <option 
                    v-for="(team,index) in gorupDpossibilities"
                    v-bind:key="index"
                  >{{team.name}}</option>
                </select>
                <span class="line"></span>
              </div>

            </div>

          </div>

        </div>

        <div class="bracket__right-result bracket__colResult-inner">

          <select v-model="semiFinals.game2Winner">

            <option 
              v-for="(team,index) in semiFinalsPossibilitiesSideB"
              v-bind:key="index"
            >{{team.name}}</option>
            
          </select>
          <span class="line"></span>
        </div>

      </div>

      <!-- WINNER -->
      <div class="bracket__center">        
        <select v-model="winner">            
          <option v-for="(team,index) in bracketData.teams" :key="index" :value="`${team}`">{{team.name}}</option>
        </select>
        <span class="line"></span>
        <p class="mb25">winner</p>
        <span class="bracketTitle">NFL Playoffs</span>
      </div>

      <!-- LEFT SIDE A - B -->
      <div class="bracket__left flexRow">

        <div class="bracket__left-matches">
          
          <div class="bracket__left-top flexRow groupA">            

            <div class="bracket__left-top-teams">
              
              <div v-for="(game,index) in bracketData.groups[0].games" v-bind:key="index" class="bracket__col flexRow">
                <div class="bracket__teams">

                  <p class="bracket__team flexRow">
                    <span class="bracket__team-title bracket__team-title-left70">{{game.team1.name}}</span>
                    <span class="bracket__teamLogo">
                      <TeamIcon :need="game.team1.name.toLowerCase()"/> {{game.team1.nodeNumber}}
                    </span>                    
                    <span class="line"></span>
                  </p>
                  <p class="bracket__team flexRow">
                    <span class="bracket__team-title bracket__team-title-left70">{{game.team2.name}}</span>
                    <span class="bracket__teamLogo">
                      <TeamIcon :need="game.team2.name.toLowerCase()"/> {{game.team2.nodeNumber}}
                    </span>                    
                    <span class="line"></span>                              
                  </p>
                </div>

                <div class="bracket__colResult bracket__colResult--border-left bracket__colResult-inner">                  
                  <select v-model="roundOf16[game.matchId].gameWinner">
                    <option :value="`${game.team1.name}`">{{game.team1.name}}</option>
                    <option :value="`${game.team2}`">{{game.team2.name}}</option>
                  </select>
                  <span class="line"></span>
                </div>
              </div>

            </div>

            <div class="bracket__right-top-result">
              <div class="bracket__right-top-result-inner bracket__right-top-result-inner--border-left">
                <select v-model="quarterFinals.game1Winner">

                  <option 
                    v-for="(team,index) in gorupApossibilities"
                    v-bind:key="index"
                  >{{team.name}}</option>
                  
                </select>
                <span class="line"></span>
              </div>
            </div>

          </div>


          <div class="bracket__left-top flexRow groupB">

            <div class="bracket__left-top-teams">
              
              <div v-for="(game,index) in bracketData.groups[1].games" v-bind:key="index" class="bracket__col flexRow">
                <div class="bracket__teams">

                  <p class="bracket__team flexRow">
                    <span class="bracket__team-title bracket__team-title-left70">{{game.team1.name}}</span>
                    <span class="bracket__teamLogo">
                      <TeamIcon :need="game.team1.name.toLowerCase()"/> {{game.team1.nodeNumber}}
                    </span>                    
                    <span class="line"></span>
                  </p>
                  <p class="bracket__team flexRow">
                    <span class="bracket__team-title bracket__team-title-left70">{{game.team2.name}}</span>
                    <span class="bracket__teamLogo">
                      <TeamIcon :need="game.team2.name.toLowerCase()"/> {{game.team2.nodeNumber}}
                    </span>                    
                    <span class="line"></span>                              
                  </p>
                </div>

                <div class="bracket__colResult bracket__colResult--border-left bracket__colResult-inner">                  
                  <select v-model="roundOf16[game.matchId].gameWinner">
                    <option :value="`${game.team1.name}`">{{game.team1.name}}</option>
                    <option :value="`${game.team2.name}`">{{game.team2.name}}</option>
                  </select>
                  <span class="line"></span>
                </div>
              </div>              

            </div>

            <div class="bracket__right-top-result">
              <div class="bracket__right-top-result-inner bracket__right-top-result-inner--border-left">
                <select v-model="quarterFinals.game2Winner">

                  <option 
                    v-for="(team,index) in gorupBpossibilities"
                    v-bind:key="index"
                  >{{team.name}}</option>
                  
                </select>
                <span class="line"></span>
              </div>
            </div>

          </div>

        </div>

        <div class="bracket__left-result bracket__colResult-inner">

          <select v-model="semiFinals.game1Winner">
            <option 
              v-for="(team,index) in semiFinalsPossibilitiesSideA"
              v-bind:key="index"
            >{{team.name}}</option>
          </select>
          <span class="line"></span>
        </div>

      </div>

    </div>
 
  </div>
</template>

<script>
import TeamIcon from './UI/Icons/TeamIcon';

export default {
  name: 'BracketWeb',
  components: {
    TeamIcon    
  },
  data(){
    return {
      bracketData: {        
        teams: [
          {name: 'Titans', group: 'A'},
          {name: 'Patriots', group: 'A'},
          {name: 'Ravens', group: 'A'},
          {name: 'Steelers', group: 'A'},
          {name: 'Chiefs', group: 'B'},
          {name: 'Chargers', group: 'B'},
          {name: 'Bills', group: 'B'},
          {name: 'Texans', group: 'B'},
          {name: 'Vikings', group: 'C'},
          {name: 'Saints', group: 'C'},
          {name: '49ers', group: 'C'},
          {name: 'Hawks', group: 'C'},
          {name: 'Packers', group: 'D'},
          {name: 'Lions', group: 'D'},
          {name: 'Hawks', group: 'D'},
          {name: 'Eagles', group: 'D'},
        ],
        groups:[
          {
            groupId: 'A',
            games: [
              {
                matchId: 0,
                team1: {
                  name: 'Titans',
                  nodeNumber: 1,
                },
                team2: {
                  name: 'Patriots',
                  nodeNumber: 2
                }
              },
              {
                matchId: 1,
                team1: {
                  name: 'Ravens',
                  nodeNumber: 3
                },
                team2: {
                  name: 'Steelers',
                  nodeNumber: 4
                }
              },
            ]
          },
          {
            groupId: 'B',
            games: [
              {
                matchId: 2,
                team1: {
                  name: 'Chiefs',
                  nodeNumber: 5,
                },
                team2: {
                  name: 'Chargers',
                  nodeNumber: 6
                }
              },
              {
                matchId: 3,
                team1: {
                  name: 'Bills',
                  nodeNumber: 7
                },
                team2: {
                  name: 'Texans',
                  nodeNumber: 8
                }
              },
            ]
          },
          {
            groupId: 'C',
            games: [
              {
                matchId: 4,
                team1: {
                  name: 'Vikings',
                  nodeNumber: 9,
                },
                team2: {
                  name: 'Saints',
                  nodeNumber: 10,
                }
              },
              {
                matchId: 5,
                team1: {
                  name: '49ers',
                  nodeNumber: 11,
                },
                team2: {
                  name: 'Hawks',
                  nodeNumber: 12
                }
              },
            ]
          },
          {
            groupId: 'D',
            games: [
              {
                matchId: 6,
                team1: {
                  name: 'Packers',
                  nodeNumber: 13
                },
                team2: {
                  name: 'Lions',
                  nodeNumber: 14
                }
              },
              {
                matchId: 7,
                team1: {
                  name: 'Hawks',
                  nodeNumber: 15
                },
                team2: {
                  name: 'Eagles',
                  nodeNumber: 16
                }
              },
            ]
          },
        ],            
      },      
      roundOf16: [
        {gameWinner: ''},
        {gameWinner: ''},
        {gameWinner: ''},
        {gameWinner: ''},
        {gameWinner: ''},
        {gameWinner: ''},
        {gameWinner: ''},
        {gameWinner: ''},
      ],
      quarterFinals: {
        game1Winner: '',
        game2Winner: '',
        game3Winner: '',
        game4Winner: '',
      },
      semiFinals: {
        game1Winner: '',
        game2Winner: '',
      },
      winner: ''
    }
  },  
  computed: {
    gorupApossibilities: function () {
      return this.bracketData.teams.filter(team => team.group === 'A')
    },
    gorupBpossibilities: function () {
      return this.bracketData.teams.filter(team => team.group === 'B')
    },
    gorupCpossibilities: function () {
      return this.bracketData.teams.filter(team => team.group === 'C')
    },
    gorupDpossibilities: function () {
      return this.bracketData.teams.filter(team => team.group === 'D')
    },
    semiFinalsPossibilitiesSideA: function () {
      return this.bracketData.teams.filter(team => team.group === 'A' || team.group === 'B')
    },
    semiFinalsPossibilitiesSideB: function () {
      return this.bracketData.teams.filter(team => team.group === 'C' || team.group === 'D')
    }
  },
}
</script>
