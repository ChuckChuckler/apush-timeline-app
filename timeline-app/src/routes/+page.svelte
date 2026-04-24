<script lang="ts">
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
</script>