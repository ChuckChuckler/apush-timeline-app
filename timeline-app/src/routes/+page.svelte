<script lang="ts">
    let includedEvents:string[]=[]

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
            "American Revolution",
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
        "1800-19":[
            "Jefferson elected",
            "Second Great Awakening begins",
            "Expansion of universal white male suffrage",
            "Temperance Movement begins",
            "Napoleonic Wars in Europe",
            "Louisiana Purchase",
            "Embargo Act",
            "Prohibition of international slave trade",
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
            "Reagen elected",
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
    }

    function include(period:string, checked:boolean){
        if(checked){
            includedEvents.push(period);
        }else{
            includedEvents.splice(includedEvents.indexOf(period),1);
        }
    }
</script>
<h1 class="text-center">Really fun practice app (so much fun)</h1>
<div class="w-[50%] m-auto">
    <div>
        <h3 class="text-center">practice type</h3>
        <div class="w-[60%] m-auto">
            <input type="radio" name="practice-type" value="learn" id="learn">
            <label for="learn">learn</label>
            <br>
            <input type="radio" name="practice-type" value="test" id="test">
            <label for="test">practice</label>
        </div>
    </div>
    <div>
        <h3 class="text-center">include events from:</h3>
        <div>
            <input type="checkbox" name="Pre-1600" id="Pre-1600" value="Pre-1600" onchange={function(){include("Pre-1600", this.checked==undefined?false:this.checked)}}>
            <label for="Pre-1600">Pre-1600</label>
            <br>
            <div>
                <input type="checkbox" name="First half of 1600s" id="First half of 1600s" value="First half of 1600s" onchange={function(){include("First half of 1600s", this.checked==undefined?false:this.checked)}}>
                <label for="First half of 1600s">First half of 1600s</label>
                <br>
                <input type="checkbox" name="Second half of 1600s" id="Second half of 1600s" value="Second half of 1600s" onchange={function(){include("Second half of 1600s", this.checked==undefined?false:this.checked)}}>
                <label for="Second half of 1600s">Second half of 1600s</label>
            </div>
            <br>
            <div>
                <input type="checkbox" name="1700-60" id="1700-60" value="1700-60" onchange={function(){include("1700-60", this.checked==undefined?false:this.checked)}}>
                <label for="1700-60">1700-60</label>
                <br>
                <input type="checkbox" name="1760-69" id="1760-69" value="1760-69" onchange={function(){include("1760-69", this.checked==undefined?false:this.checked)}}>
                <label for="1760-69">1760-69</label>
                <br>
                <input type="checkbox" name="1770-79" id="1770-79" value="1770-79" onchange={function(){include("1770-79", this.checked==undefined?false:this.checked)}}>
                <label for="1770-79">1770-79</label>
                <br>
                <input type="checkbox" name="1780-89" id="1780-89" value="1780-89" onchange={function(){include("1780-89", this.checked==undefined?false:this.checked)}}>
                <label for="1780-89">1780-89</label>
                <br>
                <input type="checkbox" name="1790-99" id="1790-99" value="1790-99" onchange={function(){include("1790-99", this.checked==undefined?false:this.checked)}}>
                <label for="1790-99">1790-99</label>
            </div>
            <br>
            <div>
                <input type="checkbox" name="1800-19" id="1800-19" value="1800-19" onchange={function(){include("1800-19", this.checked==undefined?false:this.checked)}}>
                <label for="1800-19">1800-19</label>
                <br>
                <input type="checkbox" name="1820-29" id="1820-29" value="1820-29" onchange={function(){include("1820-29", this.checked==undefined?false:this.checked)}}>
                <label for="1820-29">1820-29</label>
                <br>
                <input type="checkbox" name="1830-39" id="1830-39" value="1830-39" onchange={function(){include("1830-39", this.checked==undefined?false:this.checked)}}>
                <label for="1830-39">1830-39</label>
                <br>
                <input type="checkbox" name="1840-49" id="1840-49" value="1840-49" onchange={function(){include("1840-49", this.checked==undefined?false:this.checked)}}>
                <label for="1840-49">1840-49</label>
                <br>
                <input type="checkbox" name="1850-59" id="1850-59" value="1850-59" onchange={function(){include("1850-59", this.checked==undefined?false:this.checked)}}>
                <label for="1850-59">1850-59</label>
                <br>
                <input type="checkbox" name="1860-69" id="1860-69" value="1860-69" onchange={function(){include("1860-69", this.checked==undefined?false:this.checked)}}>
                <label for="1860-69">1860-69</label>
                <br>
                <input type="checkbox" name="1870-79" id="1870-79" value="1870-79" onchange={function(){include("1870-79", this.checked==undefined?false:this.checked)}}>
                <label for="1870-79">1870-79</label>
                <br>
                <input type="checkbox" name="1880-89" id="1880-89" value="1880-89" onchange={function(){include("1880-89", this.checked==undefined?false:this.checked)}}>
                <label for="1880-89">1880-89</label>
                <br>
                <input type="checkbox" name="1890-99" id="1890-99" value="1890-99" onchange={function(){include("1890-99", this.checked==undefined?false:this.checked)}}>
                <label for="1890-99">1890-99</label>
            </div>
            <br>
            <div>
                <input type="checkbox" name="1900-09" id="1900-09" value="1900-09" onchange={function(){include("1900-09", this.checked==undefined?false:this.checked)}}>
                <label for="1900-09">1900-09</label>
                <br>
                <input type="checkbox" name="1910-19" id="1910-19" value="1910-19" onchange={function(){include("1910-19", this.checked==undefined?false:this.checked)}}>
                <label for="1910-19">1910-19</label>
                <br>
                <input type="checkbox" name="1920-29" id="1920-29" value="1920-29" onchange={function(){include("1920-29", this.checked==undefined?false:this.checked)}}>
                <label for="1920-29">1920-29</label>
                <br>
                <input type="checkbox" name="1930-39" id="1930-39" value="1930-39" onchange={function(){include("1930-39", this.checked==undefined?false:this.checked)}}>
                <label for="1930-09">1930-39</label>
                <br>
                <input type="checkbox" name="1940-49" id="1940-49" value="1940-49" onchange={function(){include("1940-49", this.checked==undefined?false:this.checked)}}>
                <label for="1940-49">1940-49</label>
                <br>
                <input type="checkbox" name="1950-59" id="1950-59" value="1950-59" onchange={function(){include("1950-59", this.checked==undefined?false:this.checked)}}>
                <label for="1950-59">1950-59</label>
                <br>
                <input type="checkbox" name="1960-69" id="1960-69" value="1960-69" onchange={function(){include("1960-69", this.checked==undefined?false:this.checked)}}>
                <label for="1960-69">1960-69</label>
                <br>
                <input type="checkbox" name="1970-79" id="1970-79" value="1970-79" onchange={function(){include("1970-79", this.checked==undefined?false:this.checked)}}>
                <label for="1970-79">1970-79</label>
                <br>
                <input type="checkbox" name="1980-89" id="1980-89" value="1980-89" onchange={function(){include("1980-89", this.checked==undefined?false:this.checked)}}>
                <label for="1980-89">1980-89</label>
                <br>
                <input type="checkbox" name="1990-99" id="1990-99" value="1990-99" onchange={function(){include("1990-99", this.checked==undefined?false:this.checked)}}>
                <label for="1990-99">1900-09</label>
            </div>
            <br>
            <input type="checkbox" name="2000-" id="2000-" value="2000-" onchange={function(){include("2000-", this.checked==undefined?false:this.checked)}}>
            <label for="2000-">2000-</label>
            <br>
        </div>
    </div>
</div>