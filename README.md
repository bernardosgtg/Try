The following diagram (**PRESS DISPLAY AT THE BOTTOM OF THE PAGE**) is both an onboarding roadmap and a procedural reference to those working on DISME:

**Before creating a new table acknowledge the [migration guidelines](https://gitlab.m-iti.org/eelab/disme/-/wikis/Database-Management#migration-guidelines-important) and [how they emerge](https://gitlab.m-iti.org/eelab/disme/-/wikis/Database-Management#disme_bd-migrations_todo-sheet) through the spreadsheet.**

```mermaid
%%{init: { 'logLevel': 'debug', 'logLevel': 'debug', 'securitylevel':'loose', "flowchart":{
      "diagramPadding":8,
"nodeSpacing":5,
"rankSpacing":20
    }} }%%
flowchart TD
id1{Are<br/>you a<br/>Novice?}--Yes-->DISMEv0.1(DISMEv0.1)
id1{Are<br/>you a<br/>Novice?}--No, returning-->id8{Questions?}

subgraph DISMEv0.1
%%{config: { 'fontFamily': 'Menlo', 'fontSize': 18, 'fontWeight': 400} }%%
id2(Necessary Software)-->id3(Create Database)
id3(Create Database)-->id4(Start using<br/>the platform)
id4(Start using<br/>the platform)-->id5(Laravel routes)
id5(Laravel routes)-->id6(Creating a new table)
id6(Creating a new table)-->id7(Creating Components)
id7(Creating Components)-->id30(Concepts<br/>and<br/>DB tables explanation)
end

DISMEv0.1(DISMEv0.1)-->id16{Are you<br/>comfortable<br/>with the core<br/>concepts?}
id16{Are you<br/>comfortable<br/>with the core<br/>concepts?}--Yes-->DISMEv0.2(DISMEv0.2)
id16{Are you<br/>comfortable<br/>with the core<br/>concepts?}--No-->DISMEv0.1(DISMEv0.1)

subgraph DISMEv0.2
    id17(DISME Initial Setup)-->id18(Clone DISMEv0.2)
    id18(Clone DISMEv0.2)-->id10(Install packages and dependencies)
    id10(Install packages<br/>and dependencies)-->id19(Create the<br/>database step 1)
    id19(Create the<br/>database step 1)-->id20(Create the<br/>database step 2)
    id20(Create the<br/>database step 2)-->id21(Run the app)
end

DISMEv0.2(DISMEv0.2)-->id22{Success?}
id22{Success?}--No-->Documentation
id22{Success?}--Yes-->DISME_Code_Development

subgraph Typescript&AngularDevelopment ["Typescript & Angular"]
    id26(Service Development)-->id27(Component Development)
end

id8{Questions?}--Yes,<br/>theoretical,<br/>DB schema<br/>or<br/>steering-related-->id9(Contact Supervisor)
id8{Questions?}--Yes,<br/>technical<br/>or<br/>development-related-->Documentation
Documentation-->id14{Still have doubts?}
id14{Still have doubts?}--Yes-->id15(Contact one of the tech leads)
id14{Still have doubts?}--No-->GitProcedure

subgraph GitProcedure [Git<br/>Procedure]
    id49{New Feature?}--Yes-->id50(Fetch and<br/>change to<br/>an existing<br/>branch where<br/>the new<br/>feature is<br/>relevant,<br/>master otherwise)
    id50(Fetch and<br/>change to<br/>an existing<br/>branch where<br/>the new<br/>feature is<br/>relevant,<br/>master otherwise)-->id52(Create new<br/>branch with<br/>the feature's<br/>name)
    id52(Create new<br/>branch with<br/>the feature's<br/>name)-->id51{Did the<br/>Supervisor<br/>request a change <br/>to the<br/>DB's schema?}
    id49{New Feature?}--No-->id51{Did the<br/>Supervisor<br/>request a change <br/>to the<br/>DB's schema?}
    id51{Did the<br/>Supervisor<br/>request a change <br/>to the<br/>DB's schema?}--Yes-->id53{Are you<br/>mid-development?}
    id51{Did the<br/>Supervisor<br/>request a change <br/>to the<br/>DB's schema?}--No-->id63(Develop)
    id53{Are you<br/>mid-development?}--Yes-->id54(Stash your changes)
    id54(Stash your changes)-->id55(Make sure<br/>you are<br/>in the<br/>correct branch)
    id55(Make sure<br/>you are<br/>in the<br/>correct branch)-->id56(Create a<br/>new migration<br/>for the<br/>requested changes)
    id56(Create a<br/>new migration<br/>for the<br/>requested changes)-->id69{Does your<br/>migration comply<br/>with the guidelines?}
    id69{Does your<br/>migration comply<br/>with the guidelines?}--Yes-->id66{Do you<br/>have pending<br/>merge requests<br/>or behind master?}
    id69{Does your<br/>migration comply<br/>with the guidelines?}--No-->id56(Create a<br/>new migration<br/>for the<br/>requested changes)
    id66{Do you<br/>have pending<br/>merge requests<br/>or behind master?}--Yes-->id67(Merge and<br/>solve conflicts<br/>for each<br/>merge request)
    id66{Do you<br/>have pending<br/>merge requests<br/>or behind master?}--No-->id57(Commit)
    id67(Merge and<br/>solve conflicts<br/>for each<br/>merge request)-->id57(Commit)
    id57(Commit)-->id58(Push)
    id58(Push)-->id71{Complying with<br/>Pre merge request<br/>Maintenance<br/>Roadmap?}
    id71{Complying with<br/>Pre merge request<br/>Maintenance<br/>Roadmap?}--No-->id63(Develop)
    id71{Complying with<br/>Pre merge request<br/>Maintenance<br/>Roadmap?}--Yes-->id59(Create a<br/>merge request<br/>from your<br/>branch to<br/>master and<br/>await the<br/>review while<br/>you continue<br/>working)
    id59(Create a<br/>merge request<br/>from your<br/>branch to<br/>master and<br/>await the<br/>review while<br/>you continue<br/>working)-.->id60{Techlead<br/>Approved?}
    id59(Create a<br/>merge request<br/>from your<br/>branch to<br/>master and<br/>await the<br/>review while<br/>you continue<br/>working)-.->id61{Did you<br/>stash?}
    id60{Techlead<br/>Approved?}--Yes-->id70(Post merge request<br/>Maintenance Roadmap)
    id70(Post merge request<br/>Maintenance Roadmap)-->id63(Develop)
    id60{Techlead<br/>Approved?}--No-->id54(Stash your changes)
    id61{Did you<br/>stash?}--Yes-->id62(Unstash)
    id61{Did you<br/>stash?}--No-->id63(Develop)
    id62(Unstash)-->id63(Develop)
    id63(Develop)<==>id64(Test:<br/>- REST API requests)
    id64(Test:<br/>- REST API requests)-->id65(Document)
    id65(Document)-->id66{Do you<br/>have pending<br/>merge requests<br/>or behind master?}

end

subgraph Documentation [Documentation]
    id11(FAQ)-.-id12(Version Control)
    id12(Version Control)-.-id13(Coding Standards)
    id13(Coding Standards)-.-id25(Go to<br/>DISME Code<br/>Development)
    id25(Go to<br/>DISME Code<br/>Development)
end

subgraph DISME_Code_Development [DISME Code Development]
    id23(Laravel-based<br/>REST API)-->id24(Tour of Heroes)
    id24(Tour of Heroes)-->Typescript&AngularDevelopment
    Typescript&AngularDevelopment--if applicable-->ActionRules
    Typescript&AngularDevelopment--if applicable-->Forms
end

subgraph ActionRules [Action Rules]
    id31(Action Rules)
%%-->id32(Action Rules'<br/>EBNF Grammar)
    %%id32(Action Rules'<br/>EBNF Grammar)-->id33(Action Rules'<br/>Database)
    %%id33(Action Rules'<br/>Database)-->id34(Integrating Blockly<br/>Library in Angular)
    %%id34(Integrating Blockly<br/>Library in Angular)-->id35(Blockly's Connection<br/>to the<br/>Project's Database)
    %%id35(Blockly's Connection<br/>to the<br/>Project's Database)-->id36(Evolution of<br/>Custom Blocks)
    %%id36(Evolution of<br/>Custom Blocks)-->id37(Blockly's<br/>Custom Blocks)
end

subgraph Forms
    id28(Forms)
%%-->id38(Form.io's<br/>Initial Integration)
    %%id38(Form.io's<br/>Initial Integration)-->id39(Database Storing)
    %%id39(Database Storing)-->id40(Form Editor's<br/>Initial Configuration)
    %%id40(Form Editor's<br/>Initial Configuration)-->id41(Customizing the<br/>Form Editor's UI)
    %%id41(Customizing the<br/>Form Editor's UI)-->id42(Auto-Loading<br/>Properties' Values)
    %%id42(Auto-Loading<br/>Properties' Values)-->id43(Editing a<br/>Created Form)
    %%id43(Editing a<br/>Created Form)-->id44(Form Render<br/>Component)
    %%id44(Form Render<br/>Component)-->id45(Client-Side<br/>Validations)
    %%id45(Client-Side<br/>Validations)-->id46(Manipulating<br/>Generated Keys)
    %%id46(Manipulating<br/>Generated-Keys)-->id47(Form.io's<br/>Translation)
    %%id47(Form.io's<br/>Translation)-->id48(Form Translator<br/>Component)
end

id9(Contact Supervisor)

%% Links
%%click id1 "" "This is a link"
click id2 "https://gitlab.m-iti.org/eelab/disme/-/wikis/necessary-software" "This is a link"
click id3 "https://gitlab.m-iti.org/eelab/disme/-/wikis/Database-Management" "This is a link"
click id4 "https://gitlab.m-iti.org/eelab/disme/-/wikis/Start-using-the-platform" "This is a link"
click id5 "https://gitlab.m-iti.org/eelab/disme/-/wikis/Laravel-routes" "This is a link"
click id6 "https://gitlab.m-iti.org/eelab/disme/-/wikis/create-table" "This is a link"
click id7 "https://gitlab.m-iti.org/eelab/disme/-/wikis/creating-components" "This is a link"
%%click id8 "" "This is a link"
%%click id9 "" "This is a link"
click id10 "https://gitlab.m-iti.org/eelab/disme/-/wikis/DISME-Initial-Setup#managing-packages-and-dependencies" "This is a link"
click id11 "https://gitlab.m-iti.org/eelab/disme/-/wikis/FAQ/FAQ-&-Errata" "This is a link"
click id12 "https://gitlab.m-iti.org/eelab/disme/-/wikis/DISME-Version-control" "This is a link"
click id13 "https://gitlab.m-iti.org/eelab/disme/-/wikis/Coding-Standards-and-Guidelines" "This is a link"
%%click id14 "" "This is a link"
%%click id15 "" "This is a link"
%%click id16 "" "This is a link"
click id17 "https://gitlab.m-iti.org/eelab/disme/-/wikis/DISME-Initial-Setup" "This is a link"
click id18 "https://gitlab.m-iti.org/eelab/disme/-/wikis/DISME-Initial-Setup#clone-the-projects-codelines" "This is a link"
click id19 "https://gitlab.m-iti.org/eelab/disme/-/wikis/DISME-Initial-Setup#create-the-database" "This is a link"
click id20 "https://gitlab.m-iti.org/eelab/disme/-/wikis/Database-Management" "This is a link"
click id21 "https://gitlab.m-iti.org/eelab/disme/-/wikis/DISME-Initial-Setup#running-the-projects" "This is a link"
%%click id22 "" "This is a link"
click id23 "https://gitlab.m-iti.org/eelab/disme/-/wikis/Laravel-API-Develpoment" "This is a link"
click id24 "https://gitlab.m-iti.org/eelab/disme/-/wikis/Typescript-Development" "This is a link"
click id25 "https://gitlab.m-iti.org/eelab/disme/-/wikis/disme-typescript-development" "This is a link"
click id26 "https://gitlab.m-iti.org/eelab/disme/-/wikis/Service-Creation" "This is a link"
click id27 "https://gitlab.m-iti.org/eelab/disme/-/wikis/Component-Creation" "This is a link"
click id28 "https://gitlab.m-iti.org/eelab/disme/-/wikis/home#forms" "This is a link"
%%click id29 "" "This is a link"
click id30 "https://gitlab.m-iti.org/eelab/disme/-/wikis/home#disme-main-concepts-and-database-tables-explanation" "This is a link"
click id31 "https://gitlab.m-iti.org/eelab/disme/-/wikis/home#action-rules" "This is a link"
%%click id32 "https://gitlab.m-iti.org/eelab/disme/-/wikis/Action-Rules/DISME-Action-Rules'-EBNF-Grammar" "This is a link"
%%click id33 "https://gitlab.m-iti.org/eelab/disme/-/wikis/Action-Rules/DISME-Action-Rules'-Database" "This is a link"
%%click id34 "https://gitlab.m-iti.org/eelab/disme/-/wikis/Action-Rules/Integrating-Blockly-Library-in-Angular" "This is a link"
%%click id35 "https://gitlab.m-iti.org/eelab/disme/-/wikis/Action-Rules/Blockly's-Connection-to-the-Project's-Database" "This is a link"
%%click id36 "https://gitlab.m-iti.org/eelab/disme/-/wikis/Action-Rules/Evolution-of-Custom-Blocks" "This is a link"
%%click id37 "https://gitlab.m-iti.org/eelab/disme/-/wikis/Action-Rules/Blockly's-Custom-Blocks" "This is a link"
%%click id38 "https://gitlab.m-iti.org/eelab/disme/-/wikis/Forms/Form.io's-Initial-Integration" "This is a link"
%%click id39 "https://gitlab.m-iti.org/eelab/disme/-/wikis/Forms/Database-Storing" "This is a link"
%%click id40 "https://gitlab.m-iti.org/eelab/disme/-/wikis/Forms/Form-Editor's-Initial-Configuration" "This is a link"
%%click id41 "https://gitlab.m-iti.org/eelab/disme/-/wikis/Forms/Customizing-the-Form-Editor's-UI" "This is a link"
%%click id42 "https://gitlab.m-iti.org/eelab/disme/-/wikis/Forms/Auto-Loading-Properties'-Values" "This is a link"
%%click id43 "https://gitlab.m-iti.org/eelab/disme/-/wikis/Forms/Editing-a-Created-Form" "This is a link"
%%click id44 "https://gitlab.m-iti.org/eelab/disme/-/wikis/Forms/Form-Render-Component" "This is a link"
%%click id45 "https://gitlab.m-iti.org/eelab/disme/-/wikis/Forms/Client-Side-Validations" "This is a link"
%%click id46 "https://gitlab.m-iti.org/eelab/disme/-/wikis/Forms/Manipulating-Generated-Keys" "This is a link"
%%click id47 "https://gitlab.m-iti.org/eelab/disme/-/wikis/Forms/Form.io's-Translation" "This is a link"
%%click id48 "https://gitlab.m-iti.org/eelab/disme/-/wikis/Forms/Form-Translator-Component" "This is a link"
%%click id49 "" "This is a link"
click id50 "https://gitlab.m-iti.org/eelab/disme/-/wikis/DISME-Version-control#branches" "This is a link"
click id51 "https://docs.google.com/spreadsheets/d/1J8UgbG-WtXDZKB1BScUZvIpww4lJ5l9VmsMzg-nnJ5o/edit#gid=1647953462" "This is a link"
click id52 "https://gitlab.m-iti.org/eelab/disme/-/wikis/DISME-Version-control#branches" "This is a link"
%%click id53 "" "This is a link"
click id54 "https://gitlab.m-iti.org/eelab/disme/-/wikis/DISME-Version-control#stashing-unstashing-apply-and-pop" "This is a link"
click id55 "https://gitlab.m-iti.org/eelab/disme/-/wikis/DISME-Version-control#branches" "This is a link"
click id56 "https://gitlab.m-iti.org/eelab/disme/-/wikis/Create-table" "This is a link"
click id57 "https://gitlab.m-iti.org/eelab/disme/-/wikis/DISME-Version-control#local-changes-and-commiting" "This is a link"
click id58 "https://gitlab.m-iti.org/eelab/disme/-/wikis/DISME-Version-Control#remote-changes-and-pushing" "This is a link"
click id59 "https://gitlab.m-iti.org/eelab/disme/-/wikis/DISME-Version-Control#create-a-merge-request" "This is a link"
%%click id60 "" "This is a link"
%%click id61 "" "This is a link"
click id62 "https://gitlab.m-iti.org/eelab/disme/-/wikis/DISME-Version-control#stashing-unstashing-apply-and-pop" "This is a link"
click id63 "https://gitlab.m-iti.org/eelab/disme/-/wikis/DISME-Development" "This is a link"
%%click id64 "" "This is a link"
%%click id65 "" "This is a link"
click id66 "https://gitlab.m-iti.org/eelab/disme/-/wikis/DISME-Version-control#merge-requests" "This is a link"
click id67 "https://gitlab.m-iti.org/eelab/disme/-/wikis/DISME-Version-control#pulling-and-solving-conflicts" "This is a link"
%%click id68 "https://gitlab.m-iti.org/eelab/disme/-/wikis/Creating-pages-with-several-languages#inserting-translations-from-json-files-into-html-and-typescript-files" "This is a link"
click id69 "https://gitlab.m-iti.org/eelab/disme/-/wikis/Database-Management#migration-guidelines-important" "This is a link"
click id70 "https://gitlab.m-iti.org/eelab/disme/-/wikis/DISME-Maintenance-roadmap#post-merge-request-maintenance-roadmap" "This is a link"
click id71 "https://gitlab.m-iti.org/eelab/disme/-/wikis/DISME-Maintenance-roadmap#pre-merge-request-maintenance-roadmap" "This is a link"


%%Style
%%style id1 text-decoration:underline,cursor:pointer,color:#1068bf
style id2 text-decoration:underline,cursor:pointer,color:#1068bf,text-decoration:underline
style id3 text-decoration:underline,cursor:pointer,color:#1068bf
style id4 text-decoration:underline,cursor:pointer,color:#1068bf
style id5 text-decoration:underline,cursor:pointer,color:#1068bf
style id6 text-decoration:underline,cursor:pointer,color:#1068bf
style id7 text-decoration:underline,cursor:pointer,color:#1068bf
%%style id8 text-decoration:underline,cursor:pointer,color:#1068bf
%%style id9 text-decoration:underline,cursor:pointer,color:#1068bf
style id10 text-decoration:underline,cursor:pointer,color:#1068bf
style id11 text-decoration:underline,cursor:pointer,color:#1068bf
style id12 text-decoration:underline,cursor:pointer,color:#1068bf
style id13 text-decoration:underline,cursor:pointer,color:#1068bf
%%style id14 text-decoration:underline,cursor:pointer,color:#1068bf
%%style id15 text-decoration:underline,cursor:pointer,color:#1068bf
%%style id16 text-decoration:underline,cursor:pointer,color:#1068bf
style id17 text-decoration:underline,cursor:pointer,color:#1068bf
style id18 text-decoration:underline,cursor:pointer,color:#1068bf
style id19 text-decoration:underline,cursor:pointer,color:#1068bf
style id20 text-decoration:underline,cursor:pointer,color:#1068bf
style id21 text-decoration:underline,cursor:pointer,color:#1068bf
%%style id22 text-decoration:underline,cursor:pointer,color:#1068bf
style id23 text-decoration:underline,cursor:pointer,color:#1068bf
style id24 text-decoration:underline,cursor:pointer,color:#1068bf
style id25 text-decoration:underline,cursor:pointer,color:#1068bf
style id26 text-decoration:underline,cursor:pointer,color:#1068bf
style id27 text-decoration:underline,cursor:pointer,color:#1068bf
style id28 text-decoration:underline,cursor:pointer,color:#1068bf
%%style id29 text-decoration:underline,cursor:pointer,color:#1068bf
style id30 text-decoration:underline,cursor:pointer,color:#1068bf
style id31 text-decoration:underline,cursor:pointer,color:#1068bf
%%style id32 text-decoration:underline,cursor:pointer,color:#1068bf
%%style id33 text-decoration:underline,cursor:pointer,color:#1068bf
%%style id34 text-decoration:underline,cursor:pointer,color:#1068bf
%%style id35 text-decoration:underline,cursor:pointer,color:#1068bf
%%style id36 text-decoration:underline,cursor:pointer,color:#1068bf
%%style id37 text-decoration:underline,cursor:pointer,color:#1068bf
%%style id38 text-decoration:underline,cursor:pointer,color:#1068bf
%%style id39 text-decoration:underline,cursor:pointer,color:#1068bf
%%style id40 text-decoration:underline,cursor:pointer,color:#1068bf
%%style id41 text-decoration:underline,cursor:pointer,color:#1068bf
%%style id42 text-decoration:underline,cursor:pointer,color:#1068bf
%%style id43 text-decoration:underline,cursor:pointer,color:#1068bf
%%style id44 text-decoration:underline,cursor:pointer,color:#1068bf
%%style id45 text-decoration:underline,cursor:pointer,color:#1068bf
%%style id46 text-decoration:underline,cursor:pointer,color:#1068bf
%%style id47 text-decoration:underline,cursor:pointer,color:#1068bf
%%style id48 text-decoration:underline,cursor:pointer,color:#1068bf
%%style id49 text-decoration:underline,cursor:pointer,color:#1068bf
style id50 text-decoration:underline,cursor:pointer,color:#1068bf
style id51 text-decoration:underline,cursor:pointer,color:#1068bf
style id52 text-decoration:underline,cursor:pointer,color:#1068bf
%%style id53 text-decoration:underline,cursor:pointer,color:#1068bf
style id54 text-decoration:underline,cursor:pointer,color:#1068bf
style id55 text-decoration:underline,cursor:pointer,color:#1068bf
style id56 text-decoration:underline,cursor:pointer,color:#1068bf
style id57 text-decoration:underline,cursor:pointer,color:#1068bf
style id58 text-decoration:underline,cursor:pointer,color:#1068bf
style id59 text-decoration:underline,cursor:pointer,color:#1068bf
%%style id60 text-decoration:underline,cursor:pointer,color:#1068bf
%%style id61 text-decoration:underline,cursor:pointer,color:#1068bf
style id62 text-decoration:underline,cursor:pointer,color:#1068bf
style id63 text-decoration:underline,cursor:pointer,color:#1068bf
%%style id64 text-decoration:underline,cursor:pointer,color:#1068bf
%%style id65 text-decoration:underline,cursor:pointer,color:#1068bf
style id66 text-decoration:underline,cursor:pointer,color:#1068bf
style id67 text-decoration:underline,cursor:pointer,color:#1068bf
%%style id68 text-decoration:underline,cursor:pointer,color:#1068bf
style id69 text-decoration:underline,cursor:pointer,color:#1068bf
style id70 text-decoration:underline,cursor:pointer,color:#1068bf
style id71 text-decoration:underline,cursor:pointer,color:#1068bf

```
