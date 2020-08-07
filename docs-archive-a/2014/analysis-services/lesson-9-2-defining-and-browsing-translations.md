---
title: 번역 정의 및 찾아보기 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0e60be99-3768-499c-a22c-a4ec37e61887
author: minewiskan
ms.author: owend
ms.openlocfilehash: 351960375ce60825dfceccaa83856545c6b9208f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734528"
---
# <a name="defining-and-browsing-translations"></a><span data-ttu-id="882c3-102">번역 정의 및 찾아보기</span><span class="sxs-lookup"><span data-stu-id="882c3-102">Defining and Browsing Translations</span></span>
  <span data-ttu-id="882c3-103">번역은 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 개체의 이름을 특정 언어로 나타내는 것을 말합니다.</span><span class="sxs-lookup"><span data-stu-id="882c3-103">A translation is a representation of the names of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] objects in a specific language.</span></span> <span data-ttu-id="882c3-104">개체에는 측정값 그룹, 측정값, 차원, 특성, 계층, KPI, 동작 및 계산 멤버가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="882c3-104">Objects include measure groups, measures, dimensions, attributes, hierarchies, KPIs, actions, and calculated members.</span></span> <span data-ttu-id="882c3-105">번역은 여러 언어를 지원할 수 있는 클라이언트 애플리케이션에 대한 서버 지원을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="882c3-105">Translations provide server support for client applications that can support multiple languages.</span></span> <span data-ttu-id="882c3-106">클라이언트는 이러한 클라이언트를 사용하여 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]인스턴스에 LCID(로캘 식별자)를 전달합니다. 그러면 해당 Analysis Services 인스턴스는 LCID를 사용하여 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 개체에 대한 메타데이터를 제공할 때 사용할 번역 집합을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="882c3-106">By using such a client, the client passes the locale identifier (LCID) to the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], which uses the LCID to determine which set of translations to use when it provides metadata for [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] objects.</span></span> <span data-ttu-id="882c3-107">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 개체에 해당 언어에 대한 번역이나 지정된 개체에 대한 번역이 없을 경우 기본 언어가 개체 메타데이터를 클라이언트에게 다시 반환하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="882c3-107">If an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object does not contain a translation for that language, or does not contain a translation for a specified object, the default language is used in returning the object metadata back to the client.</span></span> <span data-ttu-id="882c3-108">예를 들어 프랑스의 비즈니스 사용자가 프랑스어로 로캘이 설정된 워크스테이션에서 큐브에 액세스하는 경우 프랑스어 번역이 있다면 이 비즈니스 사용자에게는 멤버 캡션과 멤버 속성 값이 프랑스어로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="882c3-108">For example, if a business user in France accesses a cube from a workstation that has a French locale setting, the business user will see the member captions and member property values in French if a French translation exists.</span></span> <span data-ttu-id="882c3-109">그러나 독일의 비즈니스 사용자가 독일어로 로캘이 설정된 워크스테이션에서 동일한 큐브에 액세스하면 해당 캡션 이름과 멤버 속성 값이 독일어로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="882c3-109">However, if a business user in Germany accesses the same cube from a workstation that has a German locale setting, the business user will see the captions names and member property values in German.</span></span> <span data-ttu-id="882c3-110">자세한 내용은 [차원 번역](multidimensional-models-olap-logical-dimension-objects/dimension-translations.md), [큐브 번역](multidimensional-models-olap-logical-cube-objects/cube-translations.md), [번역 &#40;Analysis Services&#41;](translations-analysis-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="882c3-110">For more information, see [Dimension Translations](multidimensional-models-olap-logical-dimension-objects/dimension-translations.md), [Cube Translations](multidimensional-models-olap-logical-cube-objects/cube-translations.md), [Translations &#40;Analysis Services&#41;](translations-analysis-services.md).</span></span>  
  
 <span data-ttu-id="882c3-111">이 항목의 태스크에서는 Date 차원의 제한된 차원 개체 집합 및 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 큐브의 큐브 개체에 대한 메타데이터 번역을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="882c3-111">In the tasks in this topic, you define metadata translations for a limited set of dimension objects in the Date dimension and cube objects in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube.</span></span> <span data-ttu-id="882c3-112">그런 후 이러한 차원 및 큐브 개체를 검색하여 메타데이터 번역을 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="882c3-112">You will then browse these dimension and cube objects to examine the metadata translations.</span></span>  
  
## <a name="specifying-translations-for-the-date-dimension-metadata"></a><span data-ttu-id="882c3-113">Date 차원 메타데이터에 대한 번역 지정</span><span class="sxs-lookup"><span data-stu-id="882c3-113">Specifying Translations for the Date Dimension Metadata</span></span>  
  
1.  <span data-ttu-id="882c3-114">**Date** 차원에 대한 차원 디자이너를 연 다음 **번역** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="882c3-114">Open Dimension Designer for the **Date** dimension, and then click the **Translations** tab.</span></span>  
  
     <span data-ttu-id="882c3-115">각 차원 개체에 대한 메타데이터가 기본 언어로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="882c3-115">The metadata in the default language for each dimension object appears.</span></span> <span data-ttu-id="882c3-116">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 큐브의 기본 언어는 영어입니다.</span><span class="sxs-lookup"><span data-stu-id="882c3-116">The default language in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube is English.</span></span>  
  
2.  <span data-ttu-id="882c3-117">**번역** 탭의 도구 모음에서 **새 번역** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="882c3-117">On the toolbar of the **Translations** tab, click the **New Translation** button.</span></span>  
  
     <span data-ttu-id="882c3-118">언어 목록이 **언어 선택** 대화 상자에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="882c3-118">A list of languages appears in the **Select Language** dialog box.</span></span>  
  
3.  <span data-ttu-id="882c3-119">**스페인어(스페인)** 를 클릭한 후 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="882c3-119">Click **Spanish (Spain)**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="882c3-120">번역할 메타데이터 개체를 스페인어로 번역하도록 정의할 수 있는 새 열이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="882c3-120">A new column appears in which you will define the Spanish translations for the metadata objects you want to translate.</span></span> <span data-ttu-id="882c3-121">이 자습서에서는 진행 과정을 보여 주기 위해 몇 개의 개체만 번역해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="882c3-121">In this tutorial, we will only translate a few objects just to illustrate the process.</span></span>  
  
4.  <span data-ttu-id="882c3-122">**번역** 탭의 도구 모음에서 **새 번역** 단추를 클릭하고 **언어 선택** 대화 상자에서 **프랑스어(프랑스)** 를 클릭한 후 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="882c3-122">On the toolbar of the **Translations** tab, click the **New Translation** button, click **French (France)** in the **Select Language** dialog box, and then click **OK**.</span></span>  
  
     <span data-ttu-id="882c3-123">프랑스어 번역을 정의할 수 있는 또 다른 언어 열이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="882c3-123">Another language column appears in which you will define French translations.</span></span>  
  
5.  <span data-ttu-id="882c3-124">**Date** 차원에 대 한 **Caption** 개체의 행에서 `Fecha` **스페인어 (스페인)** 번역 열과 `Temps` **프랑스어 (프랑스)** 번역 열에을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="882c3-124">In the row for the **Caption** object for the **Date** dimension, type `Fecha` in the **Spanish (Spain)** translation column and `Temps` in the **French (France)** translation column.</span></span>  
  
6.  <span data-ttu-id="882c3-125">**Month Name** 특성에 대 한 **Caption** 개체의 행에서 `Mes del Año` **스페인어 (스페인)** 번역 열을 입력 하 고 `Mois d'Année` **프랑스어 (프랑스)** 번역 열에을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="882c3-125">In the row for the **Caption** object for the **Month Name** attribute, type `Mes del Año` in the **Spanish (Spain)** translation column and `Mois d'Année` in the **French (France)** translation column.</span></span>  
  
     <span data-ttu-id="882c3-126">이러한 번역을 입력 하면 줄임표 (**...**)가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="882c3-126">Notice that when you enter these translations, an ellipsis (**...**) appears.</span></span> <span data-ttu-id="882c3-127">이 줄임표를 클릭하면 특성 계층의 각 멤버에 대한 번역을 제공하는 기본 테이블의 열을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="882c3-127">Clicking this ellipsis will enable you to specify a column in the underlying table that provides translations for each member of the attribute hierarchy.</span></span>  
  
7.  <span data-ttu-id="882c3-128">**Month Name** 특성의 **스페인어 (스페인)** 번역에 대 한 줄임표 (**...**)를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="882c3-128">Click the ellipsis (**...**) for the **Spanish (Spain)** translation for the **Month Name** attribute.</span></span>  
  
     <span data-ttu-id="882c3-129">**특성 데이터 번역** 대화 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="882c3-129">The **Attribute Data Translation** dialog box appears.</span></span>  
  
8.  <span data-ttu-id="882c3-130">다음 그림에 표시된 것처럼 **번역 열** 목록에서 **SpanishMonthName**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="882c3-130">In the **Translation columns** list, select **SpanishMonthName**, as shown in the following image.</span></span>  
  
     <span data-ttu-id="882c3-131">![특성 데이터 번역 대화 상자](../../2014/tutorials/media/l9-translations-4.gif "특성 데이터 번역 대화 상자")</span><span class="sxs-lookup"><span data-stu-id="882c3-131">![Attribute Data Translation dialog box](../../2014/tutorials/media/l9-translations-4.gif "Attribute Data Translation dialog box")</span></span>  
  
9. <span data-ttu-id="882c3-132">**확인**을 클릭 한 다음 **Month Name** 특성의 **프랑스어 (프랑스)** 번역에 대 한 줄임표 (**...**)를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="882c3-132">Click **OK**, and then click the ellipsis (**...**) for the **French (France)** translation for the **Month Name** attribute.</span></span>  
  
10. <span data-ttu-id="882c3-133">**번역 열** 목록에서 **FrenchMonthName**을 선택한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="882c3-133">In the **Translation columns** list, select **FrenchMonthName**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="882c3-134">이 절차의 단계는 차원 개체 및 멤버에 대한 메타데이터 번역을 정의하는 과정을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="882c3-134">The steps in this procedure illustrate the process of defining metadata translations for dimension objects and members.</span></span>  
  
## <a name="specifying-translations-for-the-analysis-services-tutorial-cube-metadata"></a><span data-ttu-id="882c3-135">Analysis Services Tutorial 큐브 메타데이터에 대한 번역 지정</span><span class="sxs-lookup"><span data-stu-id="882c3-135">Specifying Translations for the Analysis Services Tutorial Cube Metadata</span></span>  
  
1.  <span data-ttu-id="882c3-136">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 큐브에 대한 큐브 디자이너로 전환한 후 **번역** 탭으로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="882c3-136">Switch to Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then switch to the **Translations** tab.</span></span>  
  
     <span data-ttu-id="882c3-137">다음 그림에 표시된 것처럼 각 큐브 개체에 대한 메타데이터가 기본 언어로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="882c3-137">The metadata in the default language for each cube object appears, as shown in the following image.</span></span> <span data-ttu-id="882c3-138">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 큐브의 기본 언어는 영어입니다.</span><span class="sxs-lookup"><span data-stu-id="882c3-138">The default language in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube is English.</span></span>  
  
     <span data-ttu-id="882c3-139">![번역 탭의 기본 언어](../../2014/tutorials/media/l9-translations-5.gif "번역 탭의 기본 언어")</span><span class="sxs-lookup"><span data-stu-id="882c3-139">![Default language in Translations tab](../../2014/tutorials/media/l9-translations-5.gif "Default language in Translations tab")</span></span>  
  
2.  <span data-ttu-id="882c3-140">**번역** 탭의 도구 모음에서 **새 번역** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="882c3-140">On the toolbar of the **Translations** tab, click the **New Translation** button.</span></span>  
  
     <span data-ttu-id="882c3-141">언어 목록이 **언어 선택** 대화 상자에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="882c3-141">A list of languages appears in the **Select Language** dialog box.</span></span>  
  
3.  <span data-ttu-id="882c3-142">**스페인어(스페인)** 를 선택한 후 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="882c3-142">Select **Spanish (Spain)**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="882c3-143">번역할 메타데이터 개체를 스페인어로 번역하도록 정의할 수 있는 새 열이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="882c3-143">A new column appears in which you will define the Spanish translations for the metadata objects you want to translate.</span></span> <span data-ttu-id="882c3-144">이 자습서에서는 진행 과정을 보여 주기 위해 몇 개의 개체만 번역해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="882c3-144">In this tutorial, we will only translate a few objects just to illustrate the process.</span></span>  
  
4.  <span data-ttu-id="882c3-145">**번역** 탭의 도구 모음에서 **새 번역** 단추를 클릭하고 **언어 선택** 대화 상자에서 **프랑스어(프랑스)** 를 선택한 후 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="882c3-145">On the toolbar of the **Translations** tab, click the **New Translation** button, select **French (France)** in the **Select Language** dialog box, and then click **OK**.</span></span>  
  
     <span data-ttu-id="882c3-146">프랑스어 번역을 정의할 수 있는 또 다른 언어 열이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="882c3-146">Another language column appears in which you will define French translations.</span></span>  
  
5.  <span data-ttu-id="882c3-147">**Date** 차원에 대 한 **Caption** 개체의 행에서 `Fecha` **스페인어 (스페인)** 번역 열과 `Temps` **프랑스어 (프랑스)** 번역 열에을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="882c3-147">In the row for the **Caption** object for the **Date** dimension, type `Fecha` in the **Spanish (Spain)** translation column and `Temps` in the **French (France)** translation column.</span></span>  
  
6.  <span data-ttu-id="882c3-148">**Internet Sales** 측정값 그룹에 대 한 **Caption** 개체의 행에서 `Ventas del lnternet` **스페인어 (스페인)** 번역 열과 `Ventes D'Internet` **프랑스어 (프랑스)** 번역 열을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="882c3-148">In the row for the **Caption** object for the **Internet Sales** measure group, type `Ventas del lnternet` in the **Spanish (Spain)** translation column and `Ventes D'Internet` in the **French (France)** translation column.</span></span>  
  
7.  <span data-ttu-id="882c3-149">Internet Sales-Sales Amount 측정값에 대 한 **Caption** 개체의 행에서 `Cantidad de las Ventas del Internet` **스페인어 (스페인)** 번역 열과 `Quantité de Ventes d'Internet` **프랑스어 (프랑스)** 번역 열을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="882c3-149">In the row for the **Caption** object for the Internet Sales-Sales Amount measure, type `Cantidad de las Ventas del Internet` in the **Spanish (Spain)** translation column and `Quantité de Ventes d'Internet` in the **French (France)** translation column.</span></span>  
  
     <span data-ttu-id="882c3-150">이 절차의 단계는 큐브 개체에 대한 메타데이터 번역을 정의하는 과정을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="882c3-150">The steps in this procedure illustrate the process of defining metadata translations for cube objects.</span></span>  
  
## <a name="browsing-the-cube-by-using-translations"></a><span data-ttu-id="882c3-151">번역을 사용하여 큐브 찾아보기</span><span class="sxs-lookup"><span data-stu-id="882c3-151">Browsing the Cube By Using Translations</span></span>  
  
1.  <span data-ttu-id="882c3-152">**빌드** 메뉴에서 **Analysis Services Tutorial 배포**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="882c3-152">On the **Build** menu, click **Deploy Analysis Services Tutorial**.</span></span>  
  
2.  <span data-ttu-id="882c3-153">배포가 성공적으로 완료되면 **브라우저** 탭으로 전환한 다음 **다시 연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="882c3-153">When deployment has successfully completed, switch to the **Browser** tab, and then click **Reconnect**.</span></span>  
  
3.  <span data-ttu-id="882c3-154">**데이터** 창에서 모든 계층 및 측정값을 제거하고 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 큐브 뷰 **목록에서** Tutorial을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="882c3-154">Remove all hierarchies and measures from the **Data** pane and select [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial in the **Perspectives** list.</span></span>  
  
4.  <span data-ttu-id="882c3-155">메타데이터 창에서 **Measures** 를 확장한 후 **Internet Sales**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="882c3-155">In the metadata pane, expand **Measures** and then expand **Internet Sales**.</span></span>  
  
     <span data-ttu-id="882c3-156">이 측정값 그룹에 **Internet Sales-Sales Amount** 측정값이 영어로 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="882c3-156">Notice that the **Internet Sales-Sales Amount** measure appears in English in this measure group.</span></span>  
  
5.  <span data-ttu-id="882c3-157">도구 모음의 **언어** 목록에서 **스페인어(스페인)** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="882c3-157">On the toolbar, select **Spanish (Spain)** in the **Language** list.</span></span>  
  
     <span data-ttu-id="882c3-158">메타데이터 창의 항목이 다시 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="882c3-158">Notice that the items in the metadata pane are repopulated.</span></span> <span data-ttu-id="882c3-159">메타데이터 창의 항목이 다시 채워지면 인터넷 판매 표시 폴더에 Internet Sales-Sales Amount 측정값이 더 이상 나타나지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="882c3-159">After the items in the metadata pane are repopulated, notice that the Internet Sales-Sales Amount measure no longer appears in the Internet Sales display folder.</span></span> <span data-ttu-id="882c3-160">대신 `Ventas del lnternet` , 다음 이미지에 표시 된 것 처럼 이라는 새 표시 폴더에 스페인어로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="882c3-160">Instead, it appears in Spanish in a new display folder named `Ventas del lnternet`, as shown in the following image.</span></span>  
  
     <span data-ttu-id="882c3-161">![다시 채워진 메타데이터 창](../../2014/tutorials/media/l9-translations-6.gif "다시 채워진 메타데이터 창")</span><span class="sxs-lookup"><span data-stu-id="882c3-161">![Repopulated metadata pane](../../2014/tutorials/media/l9-translations-6.gif "Repopulated metadata pane")</span></span>  
  
6.  <span data-ttu-id="882c3-162">메타 데이터 창에서를 마우스 오른쪽 단추로 클릭 하 `Cantidad de las Ventas del Internet` 고 **쿼리에 추가를**선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="882c3-162">In the metadata pane, right-click `Cantidad de las Ventas del Internet` and then select **Add to Query**.</span></span>  
  
7.  <span data-ttu-id="882c3-163">메타 데이터 창에서 Fecha를 확장 하 고 `Fecha` **Fecha**를 마우스 오른쪽 단추로 클릭 한 다음 **Fecha.Calendar Date** **필터에 추가**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="882c3-163">In the metadata pane, expand `Fecha`, expand **Fecha.Calendar Date**, right-click **Fecha.Calendar Date**, and then select **Add to Filter**.</span></span>  
  
8.  <span data-ttu-id="882c3-164">**필터** 창에서 **CY 2007** 을 필터 식으로 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="882c3-164">In the **Filter** pane, select **CY 2007** as the filter expression.</span></span>  
  
9. <span data-ttu-id="882c3-165">메타데이터 창에서 **Mes del Ano** 를 마우스 오른쪽 단추로 클릭하고 **쿼리에 추가**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="882c3-165">In the metadata pane, right-click **Mes del Ano** and select **Add to Query**.</span></span>  
  
     <span data-ttu-id="882c3-166">다음 그림에 표시된 것처럼 월 이름이 스페인어로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="882c3-166">Notice that the month names appear in Spanish, as shown in the following image.</span></span>  
  
     <span data-ttu-id="882c3-167">![데이터 창에 스페인어로 표시된 월 이름](../../2014/tutorials/media/l9-translations-7.gif "데이터 창에 스페인어로 표시된 월 이름")</span><span class="sxs-lookup"><span data-stu-id="882c3-167">![Month names in Spanish in data pane](../../2014/tutorials/media/l9-translations-7.gif "Month names in Spanish in data pane")</span></span>  
  
10. <span data-ttu-id="882c3-168">도구 모음의 **언어** 목록에서 **프랑스어(프랑스)** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="882c3-168">On the toolbar, select **French (France)** in the **Language** list.</span></span>  
  
     <span data-ttu-id="882c3-169">이제 월 이름과 측정값 이름이 프랑스어로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="882c3-169">Notice that the month names now appear in French and that the measure name now also appears in French.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="882c3-170">다음 단원</span><span class="sxs-lookup"><span data-stu-id="882c3-170">Next Lesson</span></span>  
 [<span data-ttu-id="882c3-171">10단원: 관리자 역할 정의</span><span class="sxs-lookup"><span data-stu-id="882c3-171">Lesson 10: Defining Administrative Roles</span></span>](lesson-10-defining-administrative-roles.md)  
  
## <a name="see-also"></a><span data-ttu-id="882c3-172">참고 항목</span><span class="sxs-lookup"><span data-stu-id="882c3-172">See Also</span></span>  
 <span data-ttu-id="882c3-173">[차원 번역](multidimensional-models-olap-logical-dimension-objects/dimension-translations.md) </span><span class="sxs-lookup"><span data-stu-id="882c3-173">[Dimension Translations](multidimensional-models-olap-logical-dimension-objects/dimension-translations.md) </span></span>  
 <span data-ttu-id="882c3-174">[큐브 번역](multidimensional-models-olap-logical-cube-objects/cube-translations.md) </span><span class="sxs-lookup"><span data-stu-id="882c3-174">[Cube Translations](multidimensional-models-olap-logical-cube-objects/cube-translations.md) </span></span>  
 [<span data-ttu-id="882c3-175">번역 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="882c3-175">Translations &#40;Analysis Services&#41;</span></span>](translations-analysis-services.md)  
  
  
