<script>
    /* ***** Properties ***** */

    const PROFICIENCY_MAX = 6;

    const PROFICIENCY_MIN = 0;

    /* ***** Properties ***** */

    export let data = {
        title: "Candle making",
        proficiency: 0
    }

    /* ***** Event Handlers ***** */

    const onClickDecrement = (event) => {
        if( PROFICIENCY_MIN < data.proficiency ) {
            data.proficiency -= 1;
        }
    };

    const onClickIncrement = (event) => {
        if( data.proficiency < PROFICIENCY_MAX ) {
            data.proficiency += 1;
        }
    };

    /* ***** Reactive Members ***** */

    $: proficiencyClassName = `level_${data.proficiency}`;

    $: proficiencyTitle = data.title;

    $: canDecrement = (PROFICIENCY_MIN < data.proficiency);

    $: canIncrement = (data.proficiency < PROFICIENCY_MAX);
</script>

<div class="skillDetail">
    <div class="skillName">{proficiencyTitle}</div>

    <div class="proficiency">
        <button on:click={onClickDecrement} disabled={!canDecrement}>-</button>
        <div class="proficiency_indicator {proficiencyClassName}"></div>
        <button on:click={onClickIncrement} disabled={!canIncrement}>+</button>
    </div>
</div>

<style lang="scss">
    $proficiencyUnit: 32;

    .skillDetail {
        display: flex;
        flex-direction: row;
        flex-grow: 4;
    }

    .skillName {
        flex-grow: 4;
        line-height: 1px * $proficiencyUnit;
        width: 100%;
    }

    .proficiency {
        display: flex;
        flex-direction: row;
        flex-grow: 1;

        button {
            height: 1px * $proficiencyUnit;
            width: 1px * $proficiencyUnit;
        }

        .proficiency_indicator {
            background-image: url('../sprites/indicators.png');
            background-repeat: no-repeat;
            background-size:100%;
            height: 1px * $proficiencyUnit;
            margin-left: auto;
            margin-right: auto;
            max-height: 1px * $proficiencyUnit;
            max-width: 3px * $proficiencyUnit;
            width: 3px * $proficiencyUnit;
        }

        .proficiency_indicator.level_1 {
            background-position-y: -1px * $proficiencyUnit;
        }

        .proficiency_indicator.level_2 {
            background-position-y: -2px * $proficiencyUnit;
        }

        .proficiency_indicator.level_3 {
            background-position-y: -3px * $proficiencyUnit;
        }

        .proficiency_indicator.level_4 {
            background-position-y: -4px * $proficiencyUnit;
        }

        .proficiency_indicator.level_5 {
            background-position-y: -5px * $proficiencyUnit;
        }

        .proficiency_indicator.level_6 {
            background-position-y: -6px * $proficiencyUnit;
        }
    }
    
    @media (min-width: 640px) {
		.skillDetail {
			max-width: 720px;
		}
	}
</style>
