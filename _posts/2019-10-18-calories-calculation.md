---
layout: post
title: The Calories Calculation
feature-img: "assets/img/portfolio/cabin.png"
img: "assets/img/p/036.jpg"
tags: [project 1, technical proficiency]
date: 2019-10-18
color: brown
---

About calories calculation there is a fomular according to [Wikepedia]('https://en.wikipedia.org/wiki/Metabolic_equivalent_of_task') states it. But the first thing I need to do is how to get Metabolic equivalent of task. The thing do not calculate by any fomular, only have a eastmate value in different exercise by different speed. So I just found some base value from the essey such as the [The Compendium of Physical Activities Tracking Guide]('http://prevention.sph.sc.edu/tools/docs/documents_compendium.pdf') below. In this case, I just pick up some value I needed it, but if we keen to get the algorithm higher level, I can improve it by some other way such as helper database or JSON or some component. Holpfully I can do that in the future.

    // MET values ref: December 2004(Reviewed 011 / 09) 2004, University of Colorado Hospital, Denver
    // http://www.ucdenver.edu/academics/colleges/medicine/sportsmed/cusm_patient_resources/Documents/Estimating%20Energy%20Expenditure.pdf
    // METS Activity Description
    // 1.0 Sitting Resting metabolic rate
    // 4.0 Bicycling<l0 mph, general leisure
    // 6.0 Bicycling 10-11.9 mph, leisure, slow, light effort
    // 8.0 Bicycling 12 - 13.9 mph, leisure, moderate effort
    // 10.0 Bicycling 14 - 15.9 mph, racing, fast, vigorous effort
    // 12.0 Bicycling 16 - 19 mph, racing / not drafting or > 19 mph drafting, very fast
    // 16.0 Bicycling > 20 mph, racing, not drafting
    // 8.0 Running 5 mph(12 min mile)
    // 9.0 Running 5.2 mph(11.5 min mile)
    // 10.0 Running 6 mph(10 min mile)
    // 11 Running 6.7 mph(9 min m mile)
    // 11.5 Running 7 mph(8.5 min mile)
    // 12.5 Running 7.5 mph(8 min mile)
    // 13.5 Running 8 mph(7.5 min mile)
    // 14.0 Running 8.6 mph(7 min mile)
    // 15.0 Running 9 mph(6.5 min mile)
    // 16.0 Running 10 mph(6 min mile)
    // 18.0 Running 10.9 mph(5.5 min mile)
    // 15.0 Running Running stairs
    // 2.5 Walking 2 mph, level slow pace, firm surface
    // 3.0 Walking 2.5 mph, firm surface
    // 3.5 Walking 3 mph, level, moderate pace, firm surface
    // 4.0 Walking 3.5 - 4 mph, level, brisk, firm surface
    // 4.5 Walking 4.5 mph, level, firm surface, very very brisk
    // 6.5 Walking race walking

```javascript
    getMET(dm, speed) {
        result = 1;
        switch (dm) {
            case 'WALKING':
                if (speed < 3.2) result = 2.5
                else if (speed < 4) result = 3
                else if (speed < 4.8) result = 3.5
                else if (speed < 6.4) result = 4
                else if (speed < 7.2) result = 4.5
                break;
            case 'BICYCLING':
                if (speed < 16) result = 4.0
                else if (speed < 19) result = 6.0
                else if (speed < 22) result = 8.0
                else if (speed < 25) result = 10.0
                else if (speed < 30) result = 12.0
                else if (speed > 32) result = 16.0
                break;
            case 'RUNNING':
                if (speed < 8) result = 8.0
                else if (speed < 8.4) result = 9.0
                else if (speed < 9.6) result = 10.0
                else if (speed < 10.7) result = 11.0
                else if (speed < 11.2) result = 11.5
                else if (speed < 12) result = 12.5
                else if (speed < 12.8) result = 13.5
                else if (speed < 13.8) result = 14.0
                else if (speed < 14.5) result = 15.0
                else if (speed < 16) result = 16.0
                else if (speed < 17.5) result = 18.0
                break;
        }
        return result;
    }
```