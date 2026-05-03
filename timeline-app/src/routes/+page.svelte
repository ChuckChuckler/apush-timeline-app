<script lang="ts">
    import Period from "$lib/comps/Period.svelte";
    import ResultPeriod from "$lib/comps/ResultPeriod.svelte";

    let includedEvents:string[]=$state([]);
    let includedPeriodsElements:any[]=$state([]);

    let display1600s:string=$state("display:none");
    let display1700s:string=$state("display:none");
    let display1800s:string=$state("display:none");
    let display1900s:string=$state("display:none");

    let events:Record<string,string[]>={
        "Pre-1600":[
            "Pre-European contact",
            "Columbus's first voyage",
            "Growth of Spanish/Portuguese colonies in Americas"
        ],
        "First half of 1600s":[
            "Enlightenment starts",
            "British settlement of Jamestown",
            "House of Burgesses",
            "arrival of first enslaved Africans in Virginia",
            "Mayflower Compact",
            "Massachusetts Bay Colony"
        ],
        "Second half of 1600s":[
            "first Navigation Acts",
            "Metacom's War",
            "Bacon's Rebellion",
            "Pueblo Revolt"
        ],
        "1700-60":[
            "First Great Awakening",
            "7 Years' War"
        ],
        "1760-69":[
            "Salutary Neglect ends",
            "Proclamation Line of 1763",
            "Sugar Act",
            "Stamp Act",
            "Townshend Acts",
        ],
        "1770-79":[
            "Boston Massacre",
            "Boston Tea Party",
            "Tea Act",
            "Intolerable Acts",
            "First Continental Congress",
            "Thomas Paine's \"Common Sense\"",
            "Lexington and Concord",
            "Revolutionary War",
            "Declaration of Independence",
            "Second Continental Congress",
            "Olive Branch Petition",
        ],
        "1780-89":[
            "Ratification of the Articles of Confederation",
            "Land Ordinance of 1785",
            "Shay's Rebellion",
            "Northwest Ordinance",
            "Constitution ratified",
            "French Revolution",
            "Washington becomes president"
        ],
        "1790-99":[
            "Naturalization Act of 1790",
            "First Bank of US created",
            "Whiskey Rebellion",
            "Invention of cotton gin"
        ],
        "1800-09":[
            "Jefferson elected",
            "Second Great Awakening begins",
            "Expansion of universal white male suffrage",
            "Temperance Movement begins",
            "Napoleonic Wars in Europe",
            "Louisiana Purchase",
            "Embargo Act",
            "Prohibition of international slave trade",
        ],
        "1810-19":[
            "First Bank of US falls",
            "Congress begins enacting American System programs",
            "Second Bank of US created"
        ],
        "1820-29":[
            "Monroe Doctrine",
            "Opening of first mill in Lowell",
            "Democratic Party founded",
            "Erie Canal completed",
            "Market Revolution starts",
            "Andrew Jackson elected"
        ],
        "1830-39":[
            "Indian Removal Act",
            "Whig Party founded",
            "Texas Revolution",
            "Panic of 1837"
        ],
        "1840-49":[
            "James K. Polk elected",
            "Brigham Young becomes leader of Latter-day Saints",
            "Mexican-American War",
            "Treaty of Guadalupe-Hidalgo",
            "Utopian Communities emerge",
            "Free Soil Party emerges",
            "Seneca Falls convention"
        ],
        "1850-59":[
            "Compromise of 1850",
            "Know-Nothing Party becomes popular",
            "Free Soil Party fades",
            "Republican Party founded",
            "Kansas-Nebraska Act",
            "Dred Scott Decision"
        ],
        "1860-69":[
            "Lincoln elected",
            "South Carolina secedes",
            "Confederacy formed",
            "Civil War",
            "Emancipation Proclamation",
            "Reconstruction begins",
            "Completion of first Transcontinental Railroad"
        ],
        "1870-79":[
            "Gilded Age begins",
            "Social Gospel movement begins",
            "Rockefeller Oil founded",
            "the New South",
            "Conviction of Boss Tweed",
            "Reconstruction ends (Rutherford B. Hayes)",
            "Carlisle Indian Industrial School opened",
        ],
        "1880-89":[
            "First references to Social Darwinism",
            "Jane Addams founds Hull House",
            "Andrew Carnegie's \"Gospel of Wealth\""
        ],
        "1890-99":[
            "Progressive Era begins",
            "Wounded Knee Massacre",
            "Changes in immigration patterns",
            "Census Bureau declares frontier closed",
            "People's Party (Populist Party) founded",
            "Carnegie Steel founded",
            "Imperial Japan emerges",
            "Plessy v. Ferguson",
            "Spanish-American War",
            "Philippine-American War"
        ],
        "1900-09":[
            "McKinley assassinated",
            "Teddy Roosevelt becomes president"
        ],
        "1910-19":[
            "Great Migration begins",
            "Woodrow Wilson elected",
            "Panama Canal completed",
            "WWI",
            "US enters WWI",
            "Russian Revolution",
            "Red Scare",
            "Red Summer"
        ],
        "1920-29":[
            "19th Amendment",
            "Roaring Twenties/Jazz Age",
            "Founding of USSR",
            "Immigration Act of 1924 (Johnsnon-Reed Act)",
            "Great Depression begins"
        ],
        "1930-39":[
            "FDR elected",
            "Hitler becomes chancellor of Germany",
            "New Deal",
            "HUAC created",
            "WWII starts"
        ],
        "1940-49":[
            "Pearl Harbor",
            "Internment of Japanese Americans",
            "Final Solution",
            "D-Day",
            "Death of FDR",
            "Truman becomes president",
            "VE Day",
            "WWII ends",
            "Hiroshima, Nagasaki",
            "Decolonization of Asian/African countries begins",
            "Baby Boom begins",
            "Cold War begins",
            "HUAC increases investigations",
            "Desegregation of Armed Forces",
            "Dixiecrats",
            "Founding of NATO",
            "People's Republic of China created",
            "USSR tests A-bomb"
        ],
        "1950-59":[
            "Korean War",
            "Joseph McCarthy makes first accusations-- McCarthyism",
            "growth of the suburbs",
            "Immigration and Nationality Act",
            "Brown v. Board of Education",
            "Civil Rights Movement starts",
            "Murder of Emmett Till",
            "Rosa Parks arrested",
            "beginning of Montgomery Bus Boycott",
            "Vietnam War starts"
        ],
        "1960-69":[
            "JFK elected",
            "Formation of SNCC",
            "FDA approves first birth control pill",
            "Freedom Riders",
            "Cuban Missile Crisis",
            "JFK assassinated",
            "LBJ becomes president",
            "March on Washington",
            "Betty Friedan's \"The Feminine Mystique\"",
            "Freedom Summer",
            "Civil Rights Act",
            "Republican Party begins Southern Strategy",
            "Tonkin Gulf Resolution",
            "LBJ begins Great Society program",
            "Immigration and Nationality Act of 1965",
            "Voting Rights Act",
            "Malcolm X assassinated",
            "Griswold v. Connecticut",
            "Riots over police brutality",
            "Chicano Movement begins",
            "Formation of Black Panthers",
            "Loving v. Virginia",
            "Women's Liberation Movement begins",
            "Asian American Movement begins",
            "MLK assassinated",
            "Civil Rights Movement ends",
            "Bobby Kennedy assassinated",
            "Nixon elected",
            "American Indian Movement begins",
            "Stonewall Uprising",
            "countercultures, youth culture, and antiwar protests"
        ],
        "1970-79":[
            "First Earth Day",
            "oil crisis; stagflation",
            "US manufacturing begins to decline",
            "Rise of Christian fundamentalism",
            "Pentagon Papers",
            "Nixon travels to China",
            "Watergate",
            "Title IX; ERA for ratification",
            "Roe v. Wade",
            "Nixon resigns",
            "Moral Majority",
            "Iran hostage crisis"
        ],
        "1980-89":[
            "Reagan elected",
            "Reaganomics",
            "AIDS epidemic"
        ],
        "1990-99":[
            "Cold War ends, Soviet Union falls",
            "Clinton impeached"
        ],
        "2000-":[
            "9/11",
            "beginning of War on Terror",
            "2008 Financial Crisis"
        ]
    };

    type eventInfo={
        reasonForDecade:string,
        desc:string
    };

    let eventsInformation:Record<string,eventInfo>={
        "British settlement of Jamestown":{
            reasonForDecade:"It helps to memorize the years of some events. Jamestown was founded in 1607 (or very early 1600s). You can use this to create a general timeline of the events that follow.\nJamestown was the first British colony in America.",
            desc:"A.k.a the settlement of the first American colony."
        },
        "House of Burgesses":{
            reasonForDecade:"The colonists were beginning to get settled in the early 1600s. So the early 1600s will be dominated by the thirteen original colonies forming and and organizing themselves (e.g. creating governments)",
            desc:"Virginia's house of government and America's first legislative house."
        },
        "arrival of first enslaved Africans in Virginia":{
            reasonForDecade:"This happened in the same year as the House of Burgesses!",
            desc:""
        },
        "Mayflower Compact":{
            reasonForDecade:"The colonists were beginning to get settled in the early 1600s. So the early 1600s will be dominated by the thirteen original colonies forming and and organizing themselves (e.g. creating governments)",
            desc:"This document established government in the Plymouth Colony. It was the first written framework of government in America."
        },
        "Massachusetts Bay Colony":{
            reasonForDecade:"The colonists were beginning to get settled in the early 1600s. So the early 1600s will be dominated by the thirteen original colonies forming and and organizing themselves (e.g. creating governments)",
            desc:"A colony established in Massachusetts"
        },
        "first Navigation Acts":{
            reasonForDecade:"",
            desc:"The first laws passed by Britain regulating trade, shipping, and commerce in America. The enforcement of these laws was lax (salutary neglect)."
        },
        "Metacom's War":{
            reasonForDecade:"It can help to group together Metacom's War, Bacon's Rebellion, and the Pueblo Revolt, as all three were rebellions involving Native American people prior to the Revolutionary War/creation of the United States.",
            desc:"A conflict between a coalition of Native Americans and New England colonists + their Native American allies. It was the last (?????? idk continue this once we have more info)"
        },
        "Bacon's Rebellion":{
            reasonForDecade:"It can help to group together Metacom's War, Bacon's Rebellion, and the Pueblo Revolt, as all three were rebellions involving Native American people prior to the Revolutionary War/creation of the United States.",
            desc:"A rebellion of oppressed/dissatisfied colonists against government officials, led by Nathanial Bacon. It resulted when William Berkeley-- governor of Virginia-- disallowed colonists from expanding into Native American land for tobacco planting."
        },
        "Pueblo Revolt":{
            reasonForDecade:"It can help to group together Metacom's War, Bacon's Rebellion, and the Pueblo Revolt, as all three were rebellions involving Native American people prior to the Revolutionary War/creation of the United States.",
            desc:"A successful revolt by the Pueblo peoples against Spanish rule. The Pueblo peoples maintained sovereignty for 12 years following this."
        },
        "First Great Awakening":{
            reasonForDecade:"",
            desc:"A key religious movement in the 1730s-40s emphasizing human sin and urging atonement. Introduced emotionalism into religious practice. Key figures include George Whitefield and Rev. Jonathan Edwards, the latter delivering the famous sermon \"Sinners in the Hands of Angry God\".",
        },
        "7 Years' War":{
            reasonForDecade:"The 7 Years' War is what led Britain to tighten its hold on the colonies. After the end of the conflict is when legislation like the Sugar and Stamp Acts were passed as Britain tried to manage war debt and new territories.",
            desc:"A conflict between France and Britain and their allies that was described by Winston Churchill as \"the first world war\". A continuation of France and Britain's struggle over territories, it was sparked by a debate over claim to the upper Ohio River valley. Following this event, Britain increased control over the colonies substantially."
        },
        "Salutary Neglect ends":{
            reasonForDecade:"This event is in the decade following the 7 Years' War. The 7 Years' War is what led to Britain tightening its control on the colonies. A good way to look at it is the 7 Years War --> Britain becoming more strict, colonists dissatisfied but not openly retaliating --> Britain going further, colonists begin to retaliate and clamor for independence = 1700-60 --> 1760-69 --> 1770-79.",
            desc:"Britain ends their practice of being lenient on their enforcement of laws. This upset colonists, as the sudden enforcement was unexpected and overly harsh."
        },
        "Proclamation Line of 1763":{
            reasonForDecade:"my guy it's literally in the name",
            desc:"Colonists wanted to move to new westward territory gained after the 7 Years' War. However, doing so would interfere with the indigenous tribes already living there. To avoid conflict, British Parliament passed the act creating this-- a boundary beyond which colonists were not allowed to settle. This angered colonists, and most did not comply, increasing tension between Britain and the American colonies."
        },
        "Sugar Act":{
            reasonForDecade:"This event is in the decade following the 7 Years' War. The 7 Years' War is what led to Britain tightening its control on the colonies. A good way to look at it is the 7 Years War --> Britain becoming more strict, colonists dissatisfied but not openly retaliating or considering independence --> Britain going further, colonists begin to retaliate and clamor for independence = 1700-60 --> 1760-69 --> 1770-79.",
            desc:"This act reduced the tax on molasses, but imposed taxes on other goods. It was an attempt to stop smuggling, severely penalizing offenders and trying them in British-run courts. It can be linked to the end of salutary neglect. This upset colonists."
        },
        "Stamp Act":{
            reasonForDecade:"This event is in the decade following the 7 Years' War. The 7 Years' War is what led to Britain tightening its control on the colonies. A good way to look at it is the 7 Years War --> Britain becoming more strict, colonists dissatisfied but not openly retaliating or considering independence --> Britain going further, colonists begin to retaliate and clamor for independence = 1700-60 --> 1760-69 --> 1770-79.",
            desc:"This act placed a tax on printed goods, including various papers, legal documents, magazines, newspapers, and playing cards. Colonists were angered by this, namely that the unfair tax was imposed on them without them being given representation in Parliament (taxation without representation)."
        },
        "Townshend Acts":{
            reasonForDecade:"This event is in the decade following the 7 Years' War. The 7 Years' War is what led to Britain tightening its control on the colonies. A good way to look at it is the 7 Years War --> Britain becoming more strict, colonists dissatisfied but not openly retaliating or considering independence --> Britain going further, colonists begin to retaliate and clamor for independence = 1700-60 --> 1760-69 --> 1770-79.",
            desc:"Four acts passed by British Parliament. The main purpose of these acts was to assert supreme authority over the colonies. They imposed duties on goods like paper, paint, and glass, and made attempts to curb smuggling and enforce new tax policies, among other things. These increased tension between the colonists and the British."
        },
        "Boston Massacre":{
            reasonForDecade:"The 1770s were the peak of colonial resistance. This is the decade when colonists were fully tired of the British and began seeing independence as an option. The Boston Massacre could be seen as the catalyst that set the path to the Revolutionary War in motion-- and it was the first major event that started off the 1770s.",
            desc:"Britain sent soldiers to Boston to enforce the Townshend Acts. After a verbal altercation between the soldiers and the colonists, the colonists began attacking the British soldiers with snowballs and stones. Eventually, one of the soldiers fired into the crowd, causing the rest of the soldiers to also begin firing without orders. Three people were instantly killed, and eight were wounded."
        },
        "Tea Act":{
            reasonForDecade:"The 1770s were the peak of colonial resistance. This is the decade when colonists were fully tired of the British and began seeing independence as an option. The Tea Act was passed before and led to the Boston Tea Party.",
            desc:"This act created a monopoly on tea dominated by the British East India Company. More importantly, although it lowered the price of tea, it maintained the taxes enforced by the Townshend Acts, implying the acceptance of \"taxation without representation\" should the colonists purchase. Many colonists understood and resented this implication."
        },
        "Boston Tea Party":{
            reasonForDecade:"The 1770s were the peak of colonial resistance. This is the decade when colonists were thoroughly frustrated with the British and began seeing independence as an option. The Boston Tea Party followed the Tea Act-- a tax on tea-- and was fueled with the resentment still simmering from the Boston Massacre. The Intolerable Acts were later passed as a response to the Boston Tea Party.",
            desc:"Angered by the Tea Act, a group of Bostonians disguised as Mohawk Indians crept aboard a British merchant ship and dumped thousands of pounds of tea into the harbor. This was illustrated as an act of patriotism by Bostonians and other colonists, and an unforgivable crime by the British."
        },
        "Intolerable Acts":{
            reasonForDecade:"The 1770s were the peak of colonial resistance. This is the decade when colonists were thoroughly frustrated with the British and began seeing independence as an option. The Intolerable Acts were passed in response to the Boston Tea Party, both to punish Massachusetts and to assert dominance over the colonies. The First Continental Congress was organized after the passage of these Acts.",
            desc:"A collection of acts created to punish Massachusetts following the Boston Tea Party. It blockaded Boston Harbor and made it virtually useless until restitution was paid for the Boston Tea Party damages and gave control of Massachusetts directly to the crown; additionally, it passed a new and more powerful Quartering Act. These acts were seen as the final straw by many."
        },
        "First Continental Congress":{
            reasonForDecade:"The 1770s were the peak of colonial resistance. This is the decade when colonists were thoroughly frustrated with the British and began seeing independence as an option. The First Continental Congress was organized as a response to the Intolerable Acts.",
            desc:"A group of delegates from every state except Georgia organized a meeting to discuss how to address and respond to Britain's increasing tyranny. They adopted the Suffolk Resolves-- which, among other things, organized a boycott of British goods until the Intolerable Acts were repealed-- and the Declaration and Resovles-- a statement including a bill of rights and a list of grievances. Neither were accepted by British Parliament."
        },
        "Thomas Paine's \"Common Sense\"":{
            reasonForDecade:"The 1770s were the peak of colonial resistance. This is the decade when colonists were thoroughly frustrated with the British and began seeing independence as an option. \"Common Sense\" was the first widely known publication that pushed independence as the only solution for the colonists' struggle and British tyranny, and it was imperative in shifting the majority of public opinion in favor of independence.",
            desc:"A publication openly criticizing the British government and emphasizing that independence was the only practical and reasonable goal the colonists should aim for. It was the first known public work to push for full-fledged independence."
        },
        "Lexington and Concord":{
            reasonForDecade:"The Revolutionary War started and ended in the 1770s, and this was its first battle. It was in the same decade as the Boston Massacre, the Boston Tea Party, and the passage of the Intolerable Acts-- all events building up to it.",
            desc:"The first battle of the Revolutionary War."
        },
        "Revolutionary War":{
            reasonForDecade:"The Revolutionary War is in the same decade as and a result of buildup from events like the Boston Massacre, the Boston Tea Party, and the Intolerable Acts.",
            desc:""
        },
        "Declaration of Independence":{
            reasonForDecade:"The Declaration of Independence was written during the Revolutionary War.",
            desc:""
        },
        "Second Continental Congress":{
            reasonForDecade:"The Second Continental Congress took place during the Revolutionary War, and was also where the Declaration of Independence was adopted.",
            desc:"A group of delegates from the thirteen colonies which functioned as the de facto government during the Revolutionary War. They wrote a number of petitions, including the Olive Branch Petition. They met continuously until past 1780."
        },
        "Olive Branch Petition":{
            reasonForDecade:"The Olive Branch Petition was written during the Second Continental Congress, which operated during the Revolutionary War.",
            desc:"A petition sent to King George III, this was the final American attempt to avoid war. It urged King George III to avoid further conflict and sought reconciliation. King George III refused to receive it."
        }
    }

    let eventsReasonDefinition
    let learnDiv:string=$state("display:none");
    let practiceDiv:string=$state("display:none");
    let resultsDiv:string=$state("display:none");
    let settingsDiv:string=$state("display:block");

    function include(period:string, checked:boolean){
        if(checked){
            includedEvents.push(period);
        }else{
            includedEvents.splice(includedEvents.indexOf(period),1);
        }
        includedEvents = sortArr(includedEvents);
        if(includedEvents.includes("Pre-1600")){
            includedEvents.splice(includedEvents.indexOf("Pre-1600"), 1);
            includedEvents.unshift("Pre-1600");
        }
    }

    let check1400s:boolean=$state(false);
    let checkAll1600s:boolean=$state(false);
    let checkAll1700s:boolean=$state(false);
    let checkAll1800s:boolean=$state(false);
    let checkAll1900s:boolean=$state(false);
    let check2000s:boolean=$state(false);

    function checkAll(century:string, checked:boolean){
        let century1600:string[] = ["First half of 1600s", "Second half of 1600s"];
        let century1700:string[] = ["1700-60", "1760-69", "1770-79", "1780-89", "1790-99"];
        let century1800:string[] = ["1800-09", "1810-19", "1820-29", "1830-39", "1840-49", "1850-59", "1860-69", "1870-79", "1880-89", "1890-99"];
        let century1900:string[] = ["1900-09", "1910-19", "1920-29", "1930-39", "1940-49", "1950-59", "1960-69", "1970-79", "1980-89", "1990-99"];

        let chosenCentury:string[] = [];

        if(century=="1600s"){
            chosenCentury=century1600;
            checked?checkAll1600s=true:checkAll1600s=false;
        }else if(century=="1700s"){
            chosenCentury=century1700;
            checked?checkAll1700s=true:checkAll1700s=false;
        }else if(century=="1800s"){
            chosenCentury=century1800;
            checked?checkAll1800s=true:checkAll1800s=false;
        }else if(century=="1900s"){
            chosenCentury=century1900;
            checked?checkAll1900s=true:checkAll1900s=false;
        }

        if(checked){
            for(let i in chosenCentury){
                includedEvents.push(chosenCentury[i]);
            }
        }else{
            for(let i in chosenCentury){
                includedEvents.splice(includedEvents.indexOf(chosenCentury[i]),1);
            }
        }

        includedEvents = sortArr(includedEvents);
        if(includedEvents.includes("Pre-1600")){
            includedEvents.splice(includedEvents.indexOf("Pre-1600"), 1);
            includedEvents.unshift("Pre-1600");
        }
    }

    function sortArr(arr:string[]){
        let arrSorted = arr.sort((a,b)=>{
            if(/^[0-9]/.test(a[0]) && !/^[0-9]/.test(b[0])) return 1;
            if(!/^[0-9]/.test(a[0]) && /^[0-9]/.test(b[0])) return -1;
            return a.localeCompare(b,undefined,{ numeric: true});
        });

        return arrSorted;
    }

    let practicedTerms:string[] = [];
    let unusedTerms:string[] = [];
    let chosenEvent:string = $state("");

    let type:any=$state();

    let clickable=$state(true);

    function startPractice(){
        if(type!="learn"){
            practiceDiv="display:block";
            settingsDiv="display:none";
            for(let i of includedEvents){
                for(let j of events[i]){
                    unusedTerms.push(j);
                }
            }

            practice("");
        }else{
            alert("Pls do practice..this feature will be implemented soon..ok? ok");
        }
    }
    
    let resultsBtn = $state("display:none");

    function practice(customTerm:string){
        if(unusedTerms.length==0){
            resultsBtn="display:block";
            chosenEvent="";
        }

        if(customTerm!==""){
            chosenEvent=customTerm;
            clickable=false;
        }else{
            unusedTerms.length==0?chosenEvent="":chosenEvent=unusedTerms[Math.floor(Math.random()*unusedTerms.length)];
        }
    }

    function classifyTerm(element:any){
        if(chosenEvent!=""){
            practicedTerms.push(chosenEvent);
            unusedTerms.indexOf(chosenEvent)==-1?unusedTerms.splice(unusedTerms.indexOf(chosenEvent),0):unusedTerms.splice(unusedTerms.indexOf(chosenEvent),1);
            element.addEvent(chosenEvent);
            clickable=true;
            practice("");
        }
    }

    let resultsPeriods:any[]=$state([]);
    
    function showResults(){
        let corrects:string[]=[];
        let incorrects:string[]=[];
        for(let i in includedEvents){
            let period = includedEvents[i];
            let periodElements = includedPeriodsElements[i].getEvents();
            for(let j of periodElements){
                if(events[period].includes(j)){
                    console.log("correct!!!");
                    corrects.push(j);
                    resultsPeriods[i].addCorrect(j);
                }else{
                    console.log("incorrect..");
                    incorrects.push(j);
                    resultsPeriods[i].addIncorrect(j);
                }
            }
        }

        practiceDiv="display:none";
        resultsDiv="display:block";
    }

    let buttonShowMissing:string=$state("display:block");
    let buttonShowIncorrect:string=$state("display:none");

    function seeCorrectPlacements(){
        for(let i of resultsPeriods){
            i.checkIncluded();
        }
        buttonShowIncorrect="display:block";
        buttonShowMissing="display:none";
    }

    function hideCorrectPlacements(){
        for(let i of resultsPeriods){
            i.showIncorrect();
        }
        buttonShowMissing="display:block";
        buttonShowIncorrect="display:none";
    }

    function showSettings(){
        settingsDiv="display:block";
        resultsDiv="display:none";
        for(let i in includedEvents){
            includedPeriodsElements[i].resetEvents();
            resultsPeriods[i].resetEvents();
        }
        practicedTerms = [];
        unusedTerms = [];
        chosenEvent = "";
        resultsBtn="display:none";
    }
</script>

<div class="bg-[#3C3B4B] h-[100vh] overflow-auto box-border p-[15px]">
    <div class="m-auto" style={settingsDiv}> <!--settings-->
        <h1 class="text-center text-[#E4E4FF] istok-web-bold text text-[25px]">APUSH Timeline Practice App</h1>
        <h3 class="text-center text-white kaisei-tokumin-regular">pre 1600s-2008</h3>
        <br>
        <div class="bg-[#616077] rounded-[20px] pt-[15px] pb-[20px] w-[50%] m-auto">
            <h3 class="text-center text-white kaisei-tokumin-regular">practice type</h3>
            <br>
            <div class="w-[60%] m-auto flex justify-around">
                <div>
                    <input class="accent-[#49437a]" type="radio" name="practice-type" value="learn" id="learn" bind:group={type} onchange={function(){alert("learn is under construction rn :p pls hold")}}>
                    <label for="learn" class="text-[#E7E7FB] text-[15px] kaisei-tokumin-regular">learn</label>
                </div>
                <div>
                    <input class="accent-[#49437a]" type="radio" name="practice-type" value="test" id="test" bind:group={type} checked={true}>
                    <label for="test" class="text-[#E7E7FB] text-[15px] kaisei-tokumin-regular">practice</label>
                </div>
            </div>
        </div>
        <br>
        <div class="bg-[#767493] rounded-[20px] w-[70%] h-[58vh] m-auto overflow-auto box-border p-[15px]"> 
            <h3 class="text-center text-white kaisei-tokumin-regular">include events from:</h3>
            <div>
                <input bind:checked={check1400s} class="accent-[#49437a]" type="checkbox" name="Pre-1600" id="Pre-1600" value="Pre-1600" onchange={function(){include("Pre-1600", this.checked==undefined?false:this.checked)}}>
                <label for="Pre-1600" class="arimo text-white text-[18px]">Pre-1600</label>
                <br>
                <br>

                <input bind:checked={checkAll1600s} class="accent-[#49437a]" type="checkbox" name="1600s" value="1600s" id="1600s" onchange={function(){this.checked==true?checkAll("1600s", true):checkAll("1600s",false)}}>
                <label for="1600s" class="arimo text-white text-[18px]">1600s</label>
                <button class="text-[12px] box-border p-[5px] text-white" onclick={function(){display1600s=="display:none"?display1600s="display:block":display1600s="display:none"}}>expand/close</button>
                <div class="bg-[#908EAC] w-[40%] rounded-[15px] box-border p-[15px]" style={display1600s}>
                    <input class="accent-[#49437a]" checked={checkAll1600s} type="checkbox" name="First half of 1600s" id="First half of 1600s" value="First half of 1600s" onchange={function(){include("First half of 1600s", this.checked==undefined?false:this.checked)}}>
                    <label class="arimo-thin text-white text-[16px]" for="First half of 1600s">First half of 1600s</label>
                    <br>
                    <input class="accent-[#49437a]" checked={checkAll1600s} type="checkbox" name="Second half of 1600s" id="Second half of 1600s" value="Second half of 1600s" onchange={function(){include("Second half of 1600s", this.checked==undefined?false:this.checked)}}>
                    <label class="arimo-thin text-white text-[16px]" for="Second half of 1600s">Second half of 1600s</label>
                </div>
                <br>
                <br>

                <input bind:checked={checkAll1700s} class="accent-[#49437a]" type="checkbox" name="1700s" id="1700s" value="1700s" onchange={function(){this.checked==true?checkAll("1700s", true):checkAll("1700s",false)}}>
                <label for="1700s" class="arimo text-white text-[18px]">1700s</label>
                <button class="text-[12px] box-border p-[5px] text-white" onclick={function(){display1700s=="display:none"?display1700s="display:block":display1700s="display:none"}}>expand/close</button>
                <div class="bg-[#908EAC] w-[40%] rounded-[15px] box-border p-[15px]" style={display1700s}>
                    <input class="accent-[#49437a]" type="checkbox" name="1700-60" id="1700-60" value="1700-60" checked={checkAll1700s} onchange={function(){include("1700-60", this.checked==undefined?false:this.checked)}}>
                    <label for="1700-60" class="arimo-thin text-white text-[16px]">1700-60</label>
                    <br>
                    <input class="accent-[#49437a]" type="checkbox" name="1760-69" id="1760-69" value="1760-69" checked={checkAll1700s} onchange={function(){include("1760-69", this.checked==undefined?false:this.checked)}}>
                    <label for="1760-69" class="arimo-thin text-white text-[16px]">1760-69</label>
                    <br>
                    <input class="accent-[#49437a]" type="checkbox" name="1770-79" id="1770-79" value="1770-79" checked={checkAll1700s} onchange={function(){include("1770-79", this.checked==undefined?false:this.checked)}}>
                    <label for="1770-79" class="arimo-thin text-white text-[16px]">1770-79</label>
                    <br>
                    <input class="accent-[#49437a]" type="checkbox" name="1780-89" id="1780-89" value="1780-89" checked={checkAll1700s} onchange={function(){include("1780-89", this.checked==undefined?false:this.checked)}}>
                    <label for="1780-89" class="arimo-thin text-white text-[16px]">1780-89</label>
                    <br>
                    <input class="accent-[#49437a]" type="checkbox" name="1790-99" id="1790-99" value="1790-99" checked={checkAll1700s} onchange={function(){include("1790-99", this.checked==undefined?false:this.checked)}}>
                    <label for="1790-99" class="arimo-thin text-white text-[16px]">1790-99</label>
                </div>
                <br>
                <br>

                <input bind:checked={checkAll1800s} class="accent-[#49437a]" type="checkbox" name="1800s" value="1800s" id="1800s" onchange={function(){this.checked==true?checkAll("1800s", true):checkAll("1800s",false)}}>
                <label for="1800s" class="arimo text-white text-[18px]">1800s</label>
                <button class="text-[12px] box-border p-[5px] text-white" onclick={function(){display1800s=="display:none"?display1800s="display:block":display1800s="display:none"}}>expand/close</button>
                <div class="bg-[#908EAC] w-[40%] rounded-[15px] box-border p-[15px]" style={display1800s}>
                    <input class="accent-[#49437a]" type="checkbox" name="1800-09" id="1800-09" value="1800-09" checked={checkAll1800s} onchange={function(){include("1800-09", this.checked==undefined?false:this.checked)}}>
                    <label class="arimo-thin text-white text-[16px]" for="1800-09">1800-09</label>
                    <br>
                    <input class="accent-[#49437a]" type="checkbox" name="1810-19" id="1810-19" value="1810-19" checked={checkAll1800s} onchange={function(){include("1810-19", this.checked==undefined?false:this.checked)}}>
                    <label class="arimo-thin text-white text-[16px]" for="1800-09">1810-19</label>
                    <br>
                    <input class="accent-[#49437a]" type="checkbox" name="1820-29" id="1820-29" value="1820-29" checked={checkAll1800s} onchange={function(){include("1820-29", this.checked==undefined?false:this.checked)}}>
                    <label class="arimo-thin text-white text-[16px]" for="1820-29">1820-29</label>
                    <br>
                    <input class="accent-[#49437a]" type="checkbox" name="1830-39" id="1830-39" value="1830-39" checked={checkAll1800s} onchange={function(){include("1830-39", this.checked==undefined?false:this.checked)}}>
                    <label class="arimo-thin text-white text-[16px]" for="1830-39">1830-39</label>
                    <br>
                    <input class="accent-[#49437a]" type="checkbox" name="1840-49" id="1840-49" value="1840-49" checked={checkAll1800s} onchange={function(){include("1840-49", this.checked==undefined?false:this.checked)}}>
                    <label class="arimo-thin text-white text-[16px]" for="1840-49">1840-49</label>
                    <br>
                    <input class="accent-[#49437a]" type="checkbox" name="1850-59" id="1850-59" value="1850-59" checked={checkAll1800s} onchange={function(){include("1850-59", this.checked==undefined?false:this.checked)}}>
                    <label class="arimo-thin text-white text-[16px]" for="1850-59">1850-59</label>
                    <br>
                    <input class="accent-[#49437a]" type="checkbox" name="1860-69" id="1860-69" value="1860-69" checked={checkAll1800s} onchange={function(){include("1860-69", this.checked==undefined?false:this.checked)}}>
                    <label class="arimo-thin text-white text-[16px]" for="1860-69">1860-69</label>
                    <br>
                    <input class="accent-[#49437a]" type="checkbox" name="1870-79" id="1870-79" value="1870-79" checked={checkAll1800s} onchange={function(){include("1870-79", this.checked==undefined?false:this.checked)}}>
                    <label class="arimo-thin text-white text-[16px]" for="1870-79">1870-79</label>
                    <br>
                    <input class="accent-[#49437a]" type="checkbox" name="1880-89" id="1880-89" value="1880-89" checked={checkAll1800s} onchange={function(){include("1880-89", this.checked==undefined?false:this.checked)}}>
                    <label class="arimo-thin text-white text-[16px]" for="1880-89">1880-89</label>
                    <br>
                    <input class="accent-[#49437a]" type="checkbox" name="1890-99" id="1890-99" value="1890-99" checked={checkAll1800s} onchange={function(){include("1890-99", this.checked==undefined?false:this.checked)}}>
                    <label class="arimo-thin text-white text-[16px]" for="1890-99">1890-99</label>
                </div>
                <br>
                <br>

                <input bind:checked={checkAll1900s} class="accent-[#49437a]" type="checkbox" name="1900s" value="1900s" id="1900s" onchange={function(){this.checked==true?checkAll("1900s", true):checkAll("1900s",false)}}>
                <label for="1900s" class="arimo text-white text-[18px]">1900s</label>
                <button class="text-[12px] box-border p-[5px] text-white" onclick={function(){display1900s=="display:none"?display1900s="display:block":display1900s="display:none"}}>expand/close</button>
                <div class="bg-[#908EAC] w-[40%] rounded-[15px] box-border p-[15px]" style={display1900s}>
                    <input class="accent-[#49437a]" type="checkbox" name="1900-09" id="1900-09" value="1900-09" checked={checkAll1900s} onchange={function(){include("1900-09", this.checked==undefined?false:this.checked)}}>
                    <label class="arimo-thin text-white text-[16px]" for="1900-09">1900-09</label>
                    <br>
                    <input class="accent-[#49437a]" type="checkbox" name="1910-19" id="1910-19" value="1910-19" checked={checkAll1900s} onchange={function(){include("1910-19", this.checked==undefined?false:this.checked)}}>
                    <label class="arimo-thin text-white text-[16px]" for="1910-19">1910-19</label>
                    <br>
                    <input class="accent-[#49437a]" type="checkbox" name="1920-29" id="1920-29" value="1920-29" checked={checkAll1900s} onchange={function(){include("1920-29", this.checked==undefined?false:this.checked)}}>
                    <label class="arimo-thin text-white text-[16px]" for="1920-29">1920-29</label>
                    <br>
                    <input class="accent-[#49437a]" type="checkbox" name="1930-39" id="1930-39" value="1930-39" checked={checkAll1900s} onchange={function(){include("1930-39", this.checked==undefined?false:this.checked)}}>
                    <label class="arimo-thin text-white text-[16px]" for="1930-09">1930-39</label>
                    <br>
                    <input class="accent-[#49437a]" type="checkbox" name="1940-49" id="1940-49" value="1940-49" checked={checkAll1900s} onchange={function(){include("1940-49", this.checked==undefined?false:this.checked)}}>
                    <label class="arimo-thin text-white text-[16px]" for="1940-49">1940-49</label>
                    <br>
                    <input class="accent-[#49437a]" type="checkbox" name="1950-59" id="1950-59" value="1950-59" checked={checkAll1900s} onchange={function(){include("1950-59", this.checked==undefined?false:this.checked)}}>
                    <label class="arimo-thin text-white text-[16px]" for="1950-59">1950-59</label>
                    <br>
                    <input class="accent-[#49437a]" type="checkbox" name="1960-69" id="1960-69" value="1960-69" checked={checkAll1900s} onchange={function(){include("1960-69", this.checked==undefined?false:this.checked)}}>
                    <label class="arimo-thin text-white text-[16px]" for="1960-69">1960-69</label>
                    <br>
                    <input class="accent-[#49437a]" type="checkbox" name="1970-79" id="1970-79" value="1970-79" checked={checkAll1900s} onchange={function(){include("1970-79", this.checked==undefined?false:this.checked)}}>
                    <label class="arimo-thin text-white text-[16px]" for="1970-79">1970-79</label>
                    <br>
                    <input class="accent-[#49437a]" type="checkbox" name="1980-89" id="1980-89" value="1980-89" checked={checkAll1900s} onchange={function(){include("1980-89", this.checked==undefined?false:this.checked)}}>
                    <label class="arimo-thin text-white text-[16px]" for="1980-89">1980-89</label>
                    <br>
                    <input class="accent-[#49437a]" type="checkbox" name="1990-99" id="1990-99" value="1990-99" checked={checkAll1900s} onchange={function(){include("1990-99", this.checked==undefined?false:this.checked)}}>
                    <label class="arimo-thin text-white text-[16px]" for="1990-99">1900-09</label>
                </div>
                <br>
                <br>

                <input bind:checked={check2000s} class="accent-[#49437a]" type="checkbox" name="2000-" id="2000-" value="2000-" onchange={function(){include("2000-", this.checked==undefined?false:this.checked)}}>
                <label for="2000-" class="arimo text-white text-[18px]">2000-</label>
                <br>
            </div>
            <button class="block m-auto bg-[#5e5c7a] text-white w-[20%] h-[30px] rounded-[15px] hover:bg-[#514f6b]" onclick={startPractice}>Go!</button>
        </div>
        <br>
    </div>

    <div class="w-[80%] h-[95vh] m-auto bg-[#767493] rounded-[20px] box-border p-[15px] overflow-auto" style={practiceDiv}> <!--events classification-->
        <h1 class="text-center kaisei-tokumin-bold text-white text-[20px]">{chosenEvent}</h1>
        <button class=" block m-auto bg-[#5e5c7a] text-white w-[20%] h-[30px] rounded-[15px] hover:bg-[#514f6b]" style={resultsBtn} onclick={showResults}>see results</button>
        <div class="grid grid-cols-3 gap-[15px] overflow-auto h-[95%] box-border p-[10px] overflow-auto">
            {#each includedEvents as period,i}
                <Period bind:this={includedPeriodsElements[i]} clickable={clickable} periodName={period} eventsAdded={[]} click={function(){classifyTerm(includedPeriodsElements[i])}} replaceEvent={practice}></Period>
            {/each}
        </div>
    </div>

    <div class="w-[80%] h-[95vh] m-auto bg-[#767493] rounded-[20px] box-border p-[15px] overflow-auto" style={resultsDiv}> <!--results-->
        <button class="block m-auto bg-[#5e5c7a] text-white w-[20%] h-[30px] rounded-[15px] hover:bg-[#514f6b]" style={buttonShowMissing} onclick={seeCorrectPlacements}>see correct placements</button>
        <button class="block m-auto bg-[#5e5c7a] text-white w-[20%] h-[30px] rounded-[15px] hover:bg-[#514f6b]" style={buttonShowIncorrect} onclick={hideCorrectPlacements}>see incorrect answers</button>
        <button class="mt-[5px] block m-auto bg-[#5e5c7a] text-white w-[20%] h-[30px] rounded-[15px] hover:bg-[#514f6b]" onclick={showSettings}>return home</button>
        <div class="grid grid-cols-3 gap-[15px] overflow-auto h-[95%] box-border p-[10px]">
            {#each includedEvents as period,i}
                <ResultPeriod bind:this={resultsPeriods[i]} periodName={period} correctEvents={[]} incorrectEvents={[]} allInPeriod={events[period]}></ResultPeriod>
            {/each}
        </div>
    </div>

    <p class="arimo-thin text-white text-center">v1.0.5</p>
    <p class="arimo-thin text-white text-center"><a class="underline" target="_blank" href="https://github.com/ChuckChuckler/apush-timeline-app">github</a>- open source, please fork!! open issue if any bugs are found</p>

</div>

<style>
    .istok-web-bold {
        font-family: "Istok Web", sans-serif;
        font-weight: 700;
        font-style: normal;
    }

    .kaisei-tokumin-regular {
        font-family: "Kaisei Tokumin", serif;
        font-weight: 400;
        font-style: normal;
    }

    .kaisei-tokumin-bold {
        font-family: "Kaisei Tokumin", serif;
        font-weight: 800;
        font-style: normal;
    }

    .arimo{
        font-family: "Arimo", sans-serif;
        font-optical-sizing: auto;
        font-weight: 600;
        font-style: normal;
    }

    .arimo-thin{
        font-family: "Arimo", sans-serif;
        font-optical-sizing: auto;
        font-weight: 400;
        font-style: normal;
    }
</style>