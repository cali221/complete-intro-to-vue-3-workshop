<script>
export default{
    props: {
        characterList: {
            type: Array,
            required: true
        }
    },
    computed: {
        characterStatistics() {
            const statuses = ['Royalty', 'Servant']
            const statistics = { Royalty: 0, Servant: 0 }
            this.characterList.forEach((character) => {
                statuses.forEach((status) => {
                if (character.status.indexOf(status) > -1) {
                    statistics[status] += 1
                }
                })
            })
            return statistics
        },
        royaltyServantPercentages() {
            const royaltiesNum = Number(this.characterStatistics.Royalty)
            const servantsNum = Number(this.characterStatistics.Servant)
            const totalCharacterNum = Number(this.characterList.length)

            const royaltyPercentage = royaltiesNum / totalCharacterNum
            const servantsPercentage = servantsNum / totalCharacterNum

            console.log(
                `Royalty Percentage: ${royaltyPercentage}, Servant Percentage: ${servantsPercentage}`,
            );

            const royaltyAndServantsPercentages = {
                Royal_Percentage: royaltyPercentage,
                Servant_Percentage: servantsPercentage,
            };

            return royaltyAndServantsPercentages;
    },
    }
}
</script>

<template>
     <h2>Statistics</h2>
    <ul>
      <li v-for="(stat, type) in characterStatistics" :key="`character-${stat}-${type}`">
        {{ type }}: {{ stat }}
      </li>
      <li v-for="(percentage, type) in royaltyServantPercentages">
        {{ type }}: {{ (percentage * 100).toFixed(2) }}%
      </li>
    </ul>
</template>