<script>
    import { text } from 'svelte/internal';

    import SkillDetail from './SkillDetail.svelte';
    import NewSkill from './NewSkill.svelte';

    const addNewSkill = (newTitle) => {
        data = [
            ...data,
            { title: newTitle, proficiency: 0}
        ];

        return(true);
    };

    // TODO: Add the rollup plugin so the test data can be pulled in via a textfile.
    
    var data = [ {
            "title": "ASP.NET (MVC and Razor)",
            "proficiency": 6
        }, {
            "title": "Autofac",
            "proficiency": 6
        }, {
            "title": "C/C++",
            "proficiency": 4
        }, {
            "title": "C#",
            "proficiency": 6
        }, {
            "title": "CSS",
            "proficiency": 5
        }, {
            "title": "Docker",
            "proficiency": 3
        }, {
            "title": "Entity Framework (4 and up)",
            "proficiency": 6
        }, {
            "title": "Golang",
            "proficiency": 3
        }, {
            "title": "HTML",
            "proficiency": 6
        }, {
            "title": "Java",
            "proficiency": 4
        }, {
            "title": "Javascript",
            "proficiency": 6
        }, {
            "title": "jQuery (plus jQuery UI)",
            "proficiency": 6
        }, {
            "title": "Knockout.JS",
            "proficiency": 6
        }, {
            "title": "Moq",
            "proficiency": 5
        }, {
            "title": "Microsoft SQL Server",
            "proficiency": 5
        }, {
            "title": "Node.JS",
            "proficiency": 2
        }, {
            "title": "NUnit",
            "proficiency": 6
        }, {
            "title": "React",
            "proficiency": 3
        }, {
            "title": "BASH Scripting",
            "proficiency": 4
        }, {
            "title": "Powershell Scripting",
            "proficiency": 6
        } ];
</script>

<div class="builder_container">
    <div class="title">Build an employee</div>

    <div class="skills_list">
        {#each data as d}
            <SkillDetail {...d} />
        {/each}
    </div>

    <div class="new_skill_panel">
        <NewSkill clbkAddSkill={addNewSkill}/>
    </div>

    <div class="footer"></div>
</div>

<style lang="scss">
    $colourMain: darkslategrey;
    $colourMainFont: white;
    $colourSecondary: lightgrey;

    .builder_container {
        border: 1px solid $colourMain;
        border-radius: 5px;
        display: flex;
        flex-direction: column;

        div {
            padding: 4px;
        }
    }

    .skills_list {
        display: flex;
        flex-direction: column;
    }

    .title {
        background-color: $colourMain;
        color: $colourMainFont;
        font-size: 1.4em;
        font-weight: bolder;
    }

    .new_skill_panel {
        background-color: $colourSecondary;
    }

    .footer {
        background-color: $colourMain;
        min-height: 6px;
    }
    
    @media (min-width: 640px) {
		.builder_container {
			max-width: 740px;
		}
	}
</style>
