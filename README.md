
# Table of Contents

1.  [Astra](#orga786c8d)
    1.  [R&D <code>[2/2]</code>](#orgf990a06)
    2.  [Stage 1 - Prep <code>[2/4]</code>](#org40375bb)
    3.  [Stage 2 - Data <code>[0/1]</code>](#org938cda5)
    4.  [Stage 3 - RL Software integrations <code>[0/2]</code>](#org8f0e890)
    5.  [Stage 4 - Operations <code>[0/2]</code>](#org75dc839)
    6.  [Stage 5 - Stream Real Time Ops <code>[0/0]</code>](#org95431f9)
    7.  [KSP Mod Requirements](#org60cbb85)
    8.  [On Hold](#org8ddfb51)



<a id="orga786c8d"></a>

# Astra


<a id="orgf990a06"></a>

## STRT R&D <code>[2/2]</code>

-   [X] Can we set up a headless/graphically limited KSP?
    -   <del>Running KSP in a VM seems promising.</del>
        -   <del>Set all graphics settings to minimum</del>
    -   We sure can! Unity options: `~KSP.x86_64 -batchmode -nographics~`
-   [X] If not headless, can we automate the launching of KSP &ldquo;instances&rdquo;, and entering/setting up the game as desired(specific missions, locations, etc.) via the [kRPC UI API](https://krpc.github.io/krpc/cpp/api/ui/ui.html)?
    -   <del>Might be able to use the Unity [Batch Mode](https://docs.unity3d.com/Manual/CLIBatchmodeCoroutines.html) and [nographics](https://docs.unity3d.com/Manual/CommandLineArguments.html) options to facilitate headless.</del>
    -   <del>Will need some means of automatically launching specified game saves.</del>
        -   <del>[AutoLoadGame](https://github.com/allista/AutoLoadGame) might do the trick.</del>
            -   <del>Might modify to use Unity CLI args instead of config file:</del>
                -   <https://answers.unity.com/questions/138715/read-command-line-arguments.html>
                -   <https://answers.unity.com/questions/366195/parameters-at-startup.html>
    -   No longer neccessary, headless is possible w/ unity opts in above task


<a id="org40375bb"></a>

## STRT Stage 1 - Prep <code>[2/4]</code>

-   [ ] Need to implement an Xvfb workflow using screenshots to debug Automation
    -   There are module load errors in KSP.log, not sure if its preventing AutoLoadGame from doing its thing, or if that is related to the Changelog startup dialog in KSP Main Menu.
    -   Why are we stuck at the Change Log dialog on KSP Start?
-   [X] Automate game-archiver
-   [-] Base VM Image(Packer) <code>[1/4]</code>
    -   [X] Install KSP 1.7.3 from S3
    -   [-] Automate mod install <code>[3/4]</code>
        -   [X] Install CKAN.deb
        -   [X] kRPC manually from github
        -   [X] AutoLoadGame - Allista
        -   [ ] RO via CKAN
    -   [ ] AutoLoadGame - Now supports specifying SFS files
    -   [ ] POC kRPC
-   [ ] Split Project into multiple repos <code>[0/2]</code>
    -   [ ] Terraform <code>[0/2]</code>
        -   [ ] Modules
        -   [ ] Plans
    -   [ ] Packer Base Image
-   [X] Choose kRPC client language - C++


<a id="org938cda5"></a>

## TODO Stage 2 - Data <code>[0/1]</code>

-   [ ] Set up client w/ all kRPC Data Stream - Once this is done, revisiting the image build will probably be worth it.
    -   Pipe into GMAT and OpenMCT ???


<a id="org8f0e890"></a>

## TODO Stage 3 - RL Software integrations <code>[0/2]</code>

-   [ ] [GMAT](https://opensource.gsfc.nasa.gov/projects/GMAT/index.php) - Planning
-   [ ] [OpenMCT](https://github.com/nasa/openmct) - Ops HUD


<a id="org75dc839"></a>

## TODO Stage 4 - Operations <code>[0/2]</code>

-   [-] Starlink(s) <code>[0/0]</code>
-   [-] Long running, real time ops <code>[0/0]</code>


<a id="org95431f9"></a>

## TODO Stage 5 - Stream Real Time Ops <code>[0/0]</code>


<a id="org60cbb85"></a>

## KSP Mod Requirements

-   [AutoLoadGame](https://github.com/allista/AutoLoadGame) - by Allista, allows creating a configuration file in your saves dir that will automatically load the specified sfs file upong game start.
-   [kRPC](https://krpc.github.io/krpc/) - kRPC allows you to control Kerbal Space Program from scripts running outside of the game.
-   [Realism Overhaul](https://github.com/KSP-RO/RealismOverhaul/wiki) - Its not certain this will place nice with [kRPC](https://krpc.github.io/krpc/), however realistic(ish?) control theory is really the purpose of this project so we will proceed with it until/unless we encounter problems.
-   [kOS](https://ksp-kos.github.io/KOS/) - kOS might be useful for some simpler tasks where we don&rsquo;t want the full power of kRPC. Might use, might not. We&rsquo;ll see.


<a id="org8ddfb51"></a>

## On Hold

-   [ ] Properly version Packer builds
    -   dev builds by commit short SHA
    -   &ldquo;Prod&rdquo; builds by Releae Tag
-   [X] Do I even want to use KSP? This [Orbiter Space flight simulator](http://orbit.medphys.ucl.ac.uk/index.html) seems interesting:
    -   Results: perhaps I&rsquo;ll work up to this at some point&#x2026;
    -   [Docs](https://www.orbiterwiki.org/wiki/)
    -   [SDK Docs](https://www.orbiterwiki.org/wiki/SDK_documentation)

