---
uid: web-pages/overview/getting-started/13-adding-social-networking-to-your-web-site
title: "将社交网络添加到 ASP.NET Web 页 (Razor) 站点 |Microsoft 文档"
author: tfitzmac
description: "本章介绍如何将您的网站与社交网络服务集成。 在本章中，你将了解如何允许用户书签/链接你的网站..."
ms.author: aspnetcontent
manager: wpickett
ms.date: 02/21/2014
ms.topic: article
ms.assetid: 03c342f9-b35c-4d7c-b9ed-cd9aaaffedb6
ms.technology: dotnet-webpages
ms.prod: .net-framework
msc.legacyurl: /web-pages/overview/getting-started/13-adding-social-networking-to-your-web-site
msc.type: authoredcontent
ms.openlocfilehash: 2c43fa7d286e43f3a4581662ce421c7435e1871f
ms.sourcegitcommit: 9a9483aceb34591c97451997036a9120c3fe2baf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/10/2017
---
<a name="adding-social-networking-to-aspnet-web-pages-razor-sites"></a><span data-ttu-id="f70f9-104">添加社交网络到 ASP.NET 网页 (Razor) 站点</span><span class="sxs-lookup"><span data-stu-id="f70f9-104">Adding Social Networking to ASP.NET Web Pages (Razor) Sites</span></span>
====================
<span data-ttu-id="f70f9-105">通过[Tom FitzMacken](https://github.com/tfitzmac)</span><span class="sxs-lookup"><span data-stu-id="f70f9-105">by [Tom FitzMacken](https://github.com/tfitzmac)</span></span>

> <span data-ttu-id="f70f9-106">此文章介绍了如何将 Facebook、 Twitter、 Reddit，和 Digg 的社交网络链接添加到在 ASP.NET Web 页 (Razor) 网站中的页以及如何包含 Twitter 源、 Xbox 游戏卡和 Gravatar 映像。</span><span class="sxs-lookup"><span data-stu-id="f70f9-106">This article explains how to add social networking links for Facebook, Twitter, Reddit, and Digg to pages in an ASP.NET Web Pages (Razor) website, and how to include Twitter feeds, Xbox gamer cards, and Gravatar images.</span></span>
> 
> <span data-ttu-id="f70f9-107">你将学习：</span><span class="sxs-lookup"><span data-stu-id="f70f9-107">What you'll learn:</span></span>
> 
> - <span data-ttu-id="f70f9-108">如何使用户可以书签/链接你的站点。</span><span class="sxs-lookup"><span data-stu-id="f70f9-108">How to let people bookmark/link your site.</span></span>
> - <span data-ttu-id="f70f9-109">如何添加 Twitter 数据源。</span><span class="sxs-lookup"><span data-stu-id="f70f9-109">How to add a Twitter feed.</span></span>
> - <span data-ttu-id="f70f9-110">如何将 Facebook 添加**如**到页的按钮。</span><span class="sxs-lookup"><span data-stu-id="f70f9-110">How to add a Facebook **Like** button to pages.</span></span>
> - <span data-ttu-id="f70f9-111">如何呈现 Gravatar.com 图像。</span><span class="sxs-lookup"><span data-stu-id="f70f9-111">How to render Gravatar.com images.</span></span>
> - <span data-ttu-id="f70f9-112">如何在你的站点上显示 Xbox 玩家卡。</span><span class="sxs-lookup"><span data-stu-id="f70f9-112">How to display an Xbox gamer card on your site.</span></span>
>   
> 
> ## <a name="software-versions-used-in-the-tutorial"></a><span data-ttu-id="f70f9-113">在本教程中使用的软件版本</span><span class="sxs-lookup"><span data-stu-id="f70f9-113">Software versions used in the tutorial</span></span>
> 
> 
> - <span data-ttu-id="f70f9-114">ASP.NET 网页 (Razor) 2</span><span class="sxs-lookup"><span data-stu-id="f70f9-114">ASP.NET Web Pages (Razor) 2</span></span>
> - <span data-ttu-id="f70f9-115">ASP.NET Web 帮助程序库 （NuGet 包）</span><span class="sxs-lookup"><span data-stu-id="f70f9-115">ASP.NET Web Helper Library (NuGet package)</span></span>
>   
> 
> <span data-ttu-id="f70f9-116">本教程还适用于 ASP.NET Web Pages 3，但使用 ASP.NET Web 帮助程序库的部分除外。</span><span class="sxs-lookup"><span data-stu-id="f70f9-116">This tutorial also works with ASP.NET Web Pages 3, except for parts that use the ASP.NET Web Helper Library.</span></span>


<a id="Linking_Your_Website"></a>
## <a name="linking-your-website-on-social-networking-sites"></a><span data-ttu-id="f70f9-117">链接您的网站上社交网络站点</span><span class="sxs-lookup"><span data-stu-id="f70f9-117">Linking Your Website on Social Networking Sites</span></span>

<span data-ttu-id="f70f9-118">如果用户喜欢上你的站点的某些内容，他们通常想要与朋友共享。</span><span class="sxs-lookup"><span data-stu-id="f70f9-118">If people like something on your site, they often want to share it with friends.</span></span> <span data-ttu-id="f70f9-119">你可以通过使其轻松显示的标志符号 （图标），用户可以单击共享 Digg、 Reddit、 Facebook、 Twitter 或类似的网站上的页面。</span><span class="sxs-lookup"><span data-stu-id="f70f9-119">You can make this easy by displaying glyphs (icons) that people can click to share a page on Digg, Reddit, Facebook, Twitter, or similar sites.</span></span>

<span data-ttu-id="f70f9-120">若要显示这些标志符号，添加`LinkSharecode`到页的帮助器。</span><span class="sxs-lookup"><span data-stu-id="f70f9-120">To display these glyphs, add the `LinkSharecode` helper to a page.</span></span> <span data-ttu-id="f70f9-121">请访问页面的人员可以单击各个标志符号。</span><span class="sxs-lookup"><span data-stu-id="f70f9-121">People who visit your page can click an individual glyph.</span></span> <span data-ttu-id="f70f9-122">如果他们具有与该社交网络站点的帐户，它们可以在该站点上中发布你的页面的链接。</span><span class="sxs-lookup"><span data-stu-id="f70f9-122">If they have an account with that social networking site, they can then post a link to your page on that site.</span></span>

![图 1](13-adding-social-networking-to-your-web-site/_static/image1.jpg)

1. <span data-ttu-id="f70f9-124">将 ASP.NET Web 帮助程序库添加到你的网站中所述[安装 ASP.NET 网页站点中的帮助器](https://go.microsoft.com/fwlink/?LinkId=252372)，如果你尚未添加它。-创建一个名为页*ListLinkShare.cshtml*并添加以下标记：</span><span class="sxs-lookup"><span data-stu-id="f70f9-124">Add the ASP.NET Web Helpers Library to your website as described in [Installing Helpers in an ASP.NET Web Pages Site](https://go.microsoft.com/fwlink/?LinkId=252372), if you haven't already added it.- Create a page named *ListLinkShare.cshtml* and add the following markup:</span></span>

    [!code-cshtml[Main](13-adding-social-networking-to-your-web-site/samples/sample1.cshtml)]

    <span data-ttu-id="f70f9-125">在此示例中，当`LinkShare`帮助程序运行，页面标题将作为一个参数，它又将传递到社交网络站点的页标题。</span><span class="sxs-lookup"><span data-stu-id="f70f9-125">In this example, when the `LinkShare` helper runs, the page title is passed as a parameter, which in turn passes the page title to the social networking site.</span></span> <span data-ttu-id="f70f9-126">但是，你无法传递所需的任何字符串。</span><span class="sxs-lookup"><span data-stu-id="f70f9-126">However, you could pass in any string you want.</span></span> <span data-ttu-id="f70f9-127">此示例还指定在列表中包括哪些社交网络站点。</span><span class="sxs-lookup"><span data-stu-id="f70f9-127">This example also specifies which social networking sites to include in the list.</span></span> <span data-ttu-id="f70f9-128">你可以指定与您的网站相关的社交网络站点。</span><span class="sxs-lookup"><span data-stu-id="f70f9-128">You can specify the social networking sites that are relevant to your site.</span></span>
- <span data-ttu-id="f70f9-129">运行*ListLinkShare.cshtml*在浏览器中的页。</span><span class="sxs-lookup"><span data-stu-id="f70f9-129">Run the *ListLinkShare.cshtml* page in a browser.</span></span> <span data-ttu-id="f70f9-130">(请确保页中选择**文件**工作区之前运行它。)</span><span class="sxs-lookup"><span data-stu-id="f70f9-130">(Make sure the page is selected in the **Files** workspace before you run it.)</span></span>
- <span data-ttu-id="f70f9-131">单击其中一个要注册的站点的字形。</span><span class="sxs-lookup"><span data-stu-id="f70f9-131">Click a glyph for one of the sites that you're signed up for.</span></span> <span data-ttu-id="f70f9-132">链接将你带到页上所选的社交网络站点在你可以共享的链接。</span><span class="sxs-lookup"><span data-stu-id="f70f9-132">The link takes you to the page on the selected social network site where you can share a link.</span></span> <span data-ttu-id="f70f9-133">例如，如果你单击 Reddit 链接，你将会转到`submit to reddit`Reddit 网站上的页面。</span><span class="sxs-lookup"><span data-stu-id="f70f9-133">For example, if you click the Reddit link, you're taken to the `submit to reddit` page on the Reddit website.</span></span>

    ![图 2](13-adding-social-networking-to-your-web-site/_static/image2.jpg)

<a id="Adding_a_Twitter_Feed"></a>
## <a name="adding-a-twitter-feed"></a><span data-ttu-id="f70f9-135">添加 Twitter 源</span><span class="sxs-lookup"><span data-stu-id="f70f9-135">Adding a Twitter Feed</span></span>

<span data-ttu-id="f70f9-136">有关使用与 Twitter API 的当前版本兼容的 Twitter 帮助的信息，请参阅[Twitter 帮助器](../ui-layouts-and-themes/twitter-helper.md)。</span><span class="sxs-lookup"><span data-stu-id="f70f9-136">For information about using a Twitter helper that is compatible with the current version of the Twitter API, see [Twitter helper](../ui-layouts-and-themes/twitter-helper.md).</span></span> <span data-ttu-id="f70f9-137">此示例演示如何编写你自己的帮助器，因此你可以轻松地重复使用很多页中的代码。</span><span class="sxs-lookup"><span data-stu-id="f70f9-137">This example shows how to write your own helper so you can easily reuse the code from many pages.</span></span>

<a id="Displaying_a_Facebook_Button"></a>
## <a name="displaying-a-facebook-quotlikequot-button"></a><span data-ttu-id="f70f9-138">显示是 Facebook&quot;如&quot;按钮</span><span class="sxs-lookup"><span data-stu-id="f70f9-138">Displaying a Facebook &quot;Like&quot; Button</span></span>

<span data-ttu-id="f70f9-139">在某些情况下，最好的选择是直接从社交网络提供程序，而不是依赖于一个帮助程序获取代码。</span><span class="sxs-lookup"><span data-stu-id="f70f9-139">In some cases, your best option is to get the code directly from the social networking provider rather than relying on a helper.</span></span> <span data-ttu-id="f70f9-140">这是如果社交网络提供商不是更新的帮助程序更快地更新其选项尤其如此。</span><span class="sxs-lookup"><span data-stu-id="f70f9-140">This is especially true if the social network provider updates its options more quickly than the helper is updated.</span></span>

<span data-ttu-id="f70f9-141">若要将 Facebook 功能 （如 Like 按钮） 添加到你的站点，你可以检索从代码段[developers.facebook.com](https://developers.facebook.com/)站点。</span><span class="sxs-lookup"><span data-stu-id="f70f9-141">To add Facebook features (such as the Like button) to your site, you can retrieve code snippets from the [developers.facebook.com](https://developers.facebook.com/) site.</span></span> <span data-ttu-id="f70f9-142">在 Facebook 站点上，你可以使用其工具生成了与你的站点相关的代码段。</span><span class="sxs-lookup"><span data-stu-id="f70f9-142">On the Facebook site, you use their tools to generate a code snippet that is relevant to your site.</span></span>

<span data-ttu-id="f70f9-143">以下突出显示的代码是 developers.facebook.com 站点上的喜欢按钮工具中检索到的代码。</span><span class="sxs-lookup"><span data-stu-id="f70f9-143">The following highlighted code is the code that was retrieved from the Like Button tool on the developers.facebook.com site.</span></span> <span data-ttu-id="f70f9-144">必须提供你自己的应用程序 id。</span><span class="sxs-lookup"><span data-stu-id="f70f9-144">You must provide your own app ID.</span></span>

[!code-html[Main](13-adding-social-networking-to-your-web-site/samples/sample2.html?highlight=7-14,16-17)]

<a id="Rendering_a_Gravatar_Image"></a>
## <a name="rendering-a-gravatar-image"></a><span data-ttu-id="f70f9-145">呈现 Gravatar 映像</span><span class="sxs-lookup"><span data-stu-id="f70f9-145">Rendering a Gravatar Image</span></span>

<span data-ttu-id="f70f9-146">A *Gravatar* (&quot;全局识别虚拟形象&quot;) 的映像，可在多个网站上作为用户标识和 #8212; 也就是说，表示你的映像。</span><span class="sxs-lookup"><span data-stu-id="f70f9-146">A *Gravatar* (a &quot;globally recognized avatar&quot;) is an image that can be used on multiple websites as your avatar &#8212; that is, an image that represents you.</span></span> <span data-ttu-id="f70f9-147">例如，Gravatar 可以识别的人员在论坛帖子，在博客注释中，依次类推。</span><span class="sxs-lookup"><span data-stu-id="f70f9-147">For example, a Gravatar can identify a person in a forum post, in a blog comment, and so on.</span></span> <span data-ttu-id="f70f9-148">(你可以注册在 Gravatar 网站在自己 Gravatar [http://www.gravatar.com/](http://www.gravatar.com/)。)如果你想要显示在网站上的人的名称或电子邮件地址旁边的图像，你可以使用 Gravatar 帮助器。</span><span class="sxs-lookup"><span data-stu-id="f70f9-148">(You can register your own Gravatar at the Gravatar website at [http://www.gravatar.com/](http://www.gravatar.com/).) If you want to display images next to people's names or email addresses on your website, you can use the Gravatar helper.</span></span>

<span data-ttu-id="f70f9-149">在此示例中，你正在使用表示自己单个 Gravatar。</span><span class="sxs-lookup"><span data-stu-id="f70f9-149">In this example, you're using a single Gravatar that represents yourself.</span></span> <span data-ttu-id="f70f9-150">使用 Gravatar 另一种是允许用户指定其 Gravatar 地址时它们在你的站点上注册。</span><span class="sxs-lookup"><span data-stu-id="f70f9-150">Another way to use a Gravatar is to let people specify their Gravatar address when they register on your site.</span></span> <span data-ttu-id="f70f9-151">(你可以了解如何使用户可以注册在[添加安全和 ASP.NET Web Pages 站点的成员资格](https://go.microsoft.com/fwlink/?LinkId=202904)。)每当显示为该用户的信息，你可以只需添加 Gravatar 到其中显示用户的名称。</span><span class="sxs-lookup"><span data-stu-id="f70f9-151">(You can learn how to let people register in [Adding Security and Membership to an ASP.NET Web Pages Site](https://go.microsoft.com/fwlink/?LinkId=202904).) Then whenever you display information for that user, you can just add the Gravatar to where you display the user's name.</span></span>

1. <span data-ttu-id="f70f9-152">将 ASP.NET Web 帮助程序库添加到你的网站中所述[安装 ASP.NET 网页站点中的帮助器](https://go.microsoft.com/fwlink/?LinkId=252372)，如果你尚未。</span><span class="sxs-lookup"><span data-stu-id="f70f9-152">Add the ASP.NET Web Helpers Library to your website as described in [Installing Helpers in an ASP.NET Web Pages Site](https://go.microsoft.com/fwlink/?LinkId=252372), if you haven't already.</span></span>
2. <span data-ttu-id="f70f9-153">创建一个名为的新 web 页*Gravatar.cshtml*。</span><span class="sxs-lookup"><span data-stu-id="f70f9-153">Create a new web page named *Gravatar.cshtml*.</span></span>
3. <span data-ttu-id="f70f9-154">将以下标记添加到文件：</span><span class="sxs-lookup"><span data-stu-id="f70f9-154">Add the following markup to the file:</span></span> 

    [!code-cshtml[Main](13-adding-social-networking-to-your-web-site/samples/sample3.cshtml)]

    <span data-ttu-id="f70f9-155">`Gravatar.GetHtml`方法在页上显示 Gravatar 的图像。</span><span class="sxs-lookup"><span data-stu-id="f70f9-155">The `Gravatar.GetHtml` method displays the Gravatar image on the page.</span></span> <span data-ttu-id="f70f9-156">若要更改图像的大小，可以作为第二个参数包含一个数字。</span><span class="sxs-lookup"><span data-stu-id="f70f9-156">To change the size of the image, you can include a number as a second parameter.</span></span> <span data-ttu-id="f70f9-157">默认大小为 80。</span><span class="sxs-lookup"><span data-stu-id="f70f9-157">The default size is 80.</span></span> <span data-ttu-id="f70f9-158">数字小于 80 使图像更小。</span><span class="sxs-lookup"><span data-stu-id="f70f9-158">Numbers less than 80 make the image smaller.</span></span> <span data-ttu-id="f70f9-159">大于 80 使图像更大的数字。</span><span class="sxs-lookup"><span data-stu-id="f70f9-159">Numbers greater than 80 make the image larger.</span></span>
4. <span data-ttu-id="f70f9-160">在`Gravatar.GetHtml`方法，将替换`<Your Gravatar account here>`用于 Gravatar 帐户的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="f70f9-160">In the `Gravatar.GetHtml` methods, replace `<Your Gravatar account here>` with the email address that you use for your Gravatar account.</span></span> <span data-ttu-id="f70f9-161">（如果你没有 Gravatar 帐户，你可以使用人员合作的电子邮件的地址）。</span><span class="sxs-lookup"><span data-stu-id="f70f9-161">(If you don't have a Gravatar account, you can use the email address of someone who does.)</span></span>
5. <span data-ttu-id="f70f9-162">在浏览器中运行页面。</span><span class="sxs-lookup"><span data-stu-id="f70f9-162">Run the page in your browser.</span></span> <span data-ttu-id="f70f9-163">该页面显示您指定的电子邮件地址的两个 Gravatar 映像。</span><span class="sxs-lookup"><span data-stu-id="f70f9-163">The page displays two Gravatar images for the email address you specified.</span></span> <span data-ttu-id="f70f9-164">第二个图像是比第一个较小。</span><span class="sxs-lookup"><span data-stu-id="f70f9-164">The second image is smaller than the first.</span></span> 

    ![图 4](13-adding-social-networking-to-your-web-site/_static/image3.jpg)

<a id="Displaying_an_Xbox_Gamer_Card"></a>
## <a name="displaying-an-xbox-gamer-card"></a><span data-ttu-id="f70f9-166">显示 Xbox 玩家卡</span><span class="sxs-lookup"><span data-stu-id="f70f9-166">Displaying an Xbox Gamer Card</span></span>

<span data-ttu-id="f70f9-167">每个用户时人游戏 Microsoft Xbox 联机，具有唯一的 id。</span><span class="sxs-lookup"><span data-stu-id="f70f9-167">When people play Microsoft Xbox games online, each user has a unique ID.</span></span> <span data-ttu-id="f70f9-168">每个玩家游戏卡中，这显示其信誉、 游戏的分数，以及最近播放游戏形式保持统计信息。</span><span class="sxs-lookup"><span data-stu-id="f70f9-168">Statistics are kept for each player in the form of a gamer card, which shows their reputation, gamer score, and recently played games.</span></span> <span data-ttu-id="f70f9-169">如果你 Xbox 游戏，你可以显示玩家卡你的站点中的网页上使用`GamerCard`帮助器。</span><span class="sxs-lookup"><span data-stu-id="f70f9-169">If you're an Xbox gamer, you can show your gamer card on pages in your site by using the `GamerCard` helper.</span></span>

1. <span data-ttu-id="f70f9-170">将 ASP.NET Web 帮助程序库添加到你的网站中所述[安装 ASP.NET 网页站点中的帮助器](https://go.microsoft.com/fwlink/?LinkId=252372)，如果你尚未。</span><span class="sxs-lookup"><span data-stu-id="f70f9-170">Add the ASP.NET Web Helpers Library to your website as described in [Installing Helpers in an ASP.NET Web Pages Site](https://go.microsoft.com/fwlink/?LinkId=252372), if you haven't already.</span></span>
2. <span data-ttu-id="f70f9-171">创建一个名为的新页*XboxGamer.cshtml*并添加以下标记。</span><span class="sxs-lookup"><span data-stu-id="f70f9-171">Create a new page named *XboxGamer.cshtml* and add the following markup.</span></span>

    [!code-cshtml[Main](13-adding-social-networking-to-your-web-site/samples/sample4.cshtml)]

    <span data-ttu-id="f70f9-172">你使用`GamerCard.GetHtml`属性来指定要显示玩家卡的别名。</span><span class="sxs-lookup"><span data-stu-id="f70f9-172">You use the `GamerCard.GetHtml` property to specify the alias for the gamer card to be displayed.</span></span>
3. <span data-ttu-id="f70f9-173">在浏览器中运行页面。</span><span class="sxs-lookup"><span data-stu-id="f70f9-173">Run the page in your browser.</span></span> <span data-ttu-id="f70f9-174">该页面显示您指定 Xbox 玩家卡。</span><span class="sxs-lookup"><span data-stu-id="f70f9-174">The page displays the Xbox gamer card that you specified.</span></span>

    ![图 5](13-adding-social-networking-to-your-web-site/_static/image4.jpg)