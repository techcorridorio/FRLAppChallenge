# PG Notes 1-27-16 on food project

1.  There's a ton of useful program information that we should take seriously, including at following links: 

[a study about participation and such](http://www.fns.usda.gov/nslpsbp-access-participation-eligibility-and-certification-study-ii)

[description of information required depending on various scenarios](https://challenges.s3.amazonaws.com/usda-school-lunch/Household%20Scenario%20Matrix.pdf)

[prototype paper application](http://nealrs.github.io/lunchuxapp/)

[definitions and explanations](http://lunchux.devpost.com/details/solver_packet)

[the sponsor's ux recommendations](http://lunchux.devpost.com/details/ux_recommendations)

[longer model application](http://www.fns.usda.gov/sites/default/files/cn/SP33-2015a4.pdf)

2.  Note that the second of these items is ambiguious in a way that doesn't matter for result but does matter for design.  If someone in a household is on public assistance *or* every student is foster/runaway/head start/migrant, then the application can cut off and solicit no further eligibility information. But there might be cases where both of those conditions apply, and we'd only need to ask about one of them. Which to ask about first?

3.  As I read the [rules](http://lunchux.devpost.com/rules) and [requirements](http://lunchux.devpost.com/details/requirements), it seems like we have to be ridiculously comprehensive in quizzing people about income sources (if we get there) in order to avoid omissions.  See ["income interview"](https://challenges.s3.amazonaws.com/usda-fns/Income%20Interview%20Examples.pdf), also see income loop discussion below.

4.  There's some boilerplate in the longer application that isn't reflected in my flowchart.  It might be best just to tack that stuff in at the end, after submission even.

## Income loop

Proposed logic, in vaguely pythonic pseudo-code, for each person (adult OR child): 

    for person in household:
        for income-source in list-of-sources:
            "does person have income-source?"
            if yes:
                does person get income-source weekly/monthy/yearly?
                how much income-source does person get [previous response frequency]?
                does person have any more of income-source?
                if yes:
                    loop around yadda yadda yadda

That will quickly get tedious, but it appears to be the requirement.

## Closing information

The closing information that's required = 
Household contact information, signature, SSN of one adult or none, and date.  This might be sensibly collected either first or last, I have it last on the flowchart.  

It might be best to squeeze disclosure boilerplate in here clickwrap style before final submission.  However, I'd worry about people thinking the application is finished and closing when they see the boilerplate rather than submission; it may be worth investigating if this can all be done *after* submission. 