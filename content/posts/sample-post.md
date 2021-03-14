---
title: "Sample Post"
date: 2021-03-13T22:08:16Z
showDate: true
draft: false
tags: ["testing"]
---

This post is purely text to prove the CD process to [Netlify](https://app.netlify.com/sites/cgc-signs/overview) is functional.

## Code

Take a look at some janky `Matlab`:

``` matlab
function out = f(obj,prop,species,T,P,RH)
    % calculate proper molal properties of fluid mixtures from nist lookup data
    if nargin < 6
        RH = 1;
    end
    % package the inputs up as a structure to allow for neat input checking
    inputname = {'T','P','RH'};
    inputdata = {T,P,RH};
    data = cell2struct(cellfun(@obj.inchk, inputdata,'un',0),inputname,2);
    % calculate mole fractions of mixture
    [comps,fracs] = obj.xn(species,data.T,data.P,data.RH);
    % calculate partial molal quantities
    fi = cellfun(@(n,x) obj.nist.f(prop,n,data.T,data.P.*x), comps,fracs,'un',0);
    % sum to proper molal quantities
    switch prop
        case 'vol' % cannot use additivity of volume because table range is for partial pressure
            % output of fi is for V not Vi - therefore mean rather than sum to output Vi
            out = mean(cell2mat(cellfun(@(n,x) n.*x, fi,fracs,'un',0)),2);
        otherwise % additivity of pressure for all other extensive properties
            out = sum(cell2mat(cellfun(@(n,x) n.*x, fi,fracs,'un',0)),2);
    end
end
```
