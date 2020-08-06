---
title: URL에 보고서 매개 변수 전달 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- URL access [Reporting Services], passing parameters
- passing parameters [Reporting Services]
ms.assetid: f93a94cc-27b5-435a-aa85-69e6ec6459ad
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: cf41ed82728d5d7c840276e135937b08f83fb131
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739514"
---
# <a name="pass-a-report-parameter-within-a-url"></a><span data-ttu-id="c4091-102">URL에 보고서 매개 변수 전달</span><span class="sxs-lookup"><span data-stu-id="c4091-102">Pass a Report Parameter Within a URL</span></span>
  <span data-ttu-id="c4091-103">보고서 매개 변수를 보고서 URL에 포함시켜 보고서에 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4091-103">You can pass report parameters to a report by including them in a report URL.</span></span> <span data-ttu-id="c4091-104">이러한 URL 매개 변수는 보고서 처리 엔진에 직접 전달되기 때문에 접두사가 붙지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c4091-104">These URL parameters are not prefixed because they are passed directly to the report processing engine.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="c4091-105">URL에는 SharePoint를 통해 요청을 라우팅하는 `_vti_bin` 프록시 구문과 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] HTTP 프록시를 포함하는 것이 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="c4091-105">It is important the URL include the `_vti_bin` proxy syntax to route the request through SharePoint and the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] HTTP proxy.</span></span> <span data-ttu-id="c4091-106">프록시는 몇 가지 컨텍스트를 HTTP 요청에 추가하며 이 컨텍스트는 SharePoint 모드 보고서 서버에 대한 보고서의 올바른 실행을 보장하는 데 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="c4091-106">The proxy adds some context to the HTTP request, context that is required to ensure proper execution of the report for SharePoint mode report servers.</span></span>  
>   
>  <span data-ttu-id="c4091-107">프록시 구문을 포함 하지 않는 경우 매개 변수를 *rp:* 로 접두사로 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4091-107">If you don't include the proxy syntax, then you need to prefix the parameter with *rp:*.</span></span>  
  
 <span data-ttu-id="c4091-108">모든 쿼리 매개 변수에는 해당하는 보고서 매개 변수가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4091-108">All query parameters can have corresponding report parameters.</span></span> <span data-ttu-id="c4091-109">해당 보고서 매개 변수를 전달하여 보고서에 쿼리 매개 변수를 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4091-109">You pass a query parameter to a report by passing the corresponding report parameter.</span></span> <span data-ttu-id="c4091-110">자세한 내용은 [관계형 쿼리 디자이너에서 쿼리 빌드&#40;보고서 작성기 및 SSRS&#41;](report-data/build-a-query-in-the-relational-query-designer-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c4091-110">For more information, see [Build a Query in the Relational Query Designer &#40;Report Builder and SSRS&#41;](report-data/build-a-query-in-the-relational-query-designer-report-builder-and-ssrs.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c4091-111">보고서 매개 변수는 대/소문자를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="c4091-111">Report parameters are case-sensitive.</span></span>  
> 
> [!NOTE]
>  <span data-ttu-id="c4091-112">보고서 매개 변수는 대/소문자를 구분하고 다음과 같은 특수 문자를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c4091-112">Report parameters are case-sensitive and utilize the following special characters:</span></span>  
> 
>  -   <span data-ttu-id="c4091-113">URL 문자열에서 공백 문자는 URL 인코딩 표준에 따라 "%20" 문자로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="c4091-113">Any space characters in the URL string are replaced with the characters "%20," according to URL encoding standards.</span></span>  
> -   <span data-ttu-id="c4091-114">URL의 매개 변수 부분에서 공백 문자는 더하기 문자(+)로 대체됩니다.</span><span class="sxs-lookup"><span data-stu-id="c4091-114">A space character in the parameter portion of the URL is replaced with a plus character (+).</span></span>  
> -   <span data-ttu-id="c4091-115">문자열의 모든 부분에서 세미콜론은 "%3A" 문자로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="c4091-115">A semicolon in any portion of the string is replaced with the characters "%3A."</span></span>  
> -   <span data-ttu-id="c4091-116">브라우저에서 적절한 URL 인코딩을 자동으로 수행하며</span><span class="sxs-lookup"><span data-stu-id="c4091-116">Browsers should automatically perform the proper URL encoding.</span></span> <span data-ttu-id="c4091-117">문자를 수동으로 인코딩할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c4091-117">You do not have to encode any of the characters manually.</span></span>  
  
 <span data-ttu-id="c4091-118">URL에 보고서 매개 변수를 설정하려면 다음 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4091-118">To set a report parameter within a URL, use the following syntax:</span></span>  
  
```  
  
parameter=value  
```  
  
 <span data-ttu-id="c4091-119">예를 들어 보고서에 정의된 두 개의 매개 변수 "ReportMonth" 및 "ReportYear"를 지정하려면 기본 모드 보고서 서버에 다음 URL을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c4091-119">For example, to specify two parameters, "ReportMonth" and "ReportYear", defined in a report, use the following URL for a native mode report server:</span></span>  
  
```  
http://myrshost/ReportServer?/AdventureWorks 2008R2/Employee_Sales_Summary_2008R2&ReportMonth=3&ReportYear=2008  
```  
  
 <span data-ttu-id="c4091-120">예를 들어 보고서에 정의된 두 개의 같은 매개 변수를 지정하려면 SharePoint 통합 모드 보고서 서버에 다음 URL을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c4091-120">For example, to specify the same two parameters defined in a report, use the following URL for a SharePoint integrated mode report server.</span></span> <span data-ttu-id="c4091-121">`/_vti_bin`을 참고하세요.</span><span class="sxs-lookup"><span data-stu-id="c4091-121">Note the `/_vti_bin`:</span></span>  
  
```  
http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/AdventureWorks 2008R2/Employee_Sales_Summary_2008R2.rdl&ReportMonth=3&ReportYear=2008  
```  
  
 <span data-ttu-id="c4091-122">매개 변수에 대해 null 값을 전달하려면 다음 구문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c4091-122">To pass a null value for a parameter, use the following syntax:</span></span>  
  
```  
  
parameter  
:isnull=true  
  
```  
  
 <span data-ttu-id="c4091-123">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c4091-123">For example,</span></span>  
  
```  
SalesOrderNumber:isnull=true  
```  
  
 <span data-ttu-id="c4091-124">`Boolean` 값을 전달하려면 False에 0을 사용하고 True에 1을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c4091-124">To pass a `Boolean` value, use 0 for false and 1 for true.</span></span> <span data-ttu-id="c4091-125">`Float` 값을 전달하려면 서버 로캘의 소수 구분 기호를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="c4091-125">To pass a `Float` value, include the decimal separator of the server locale</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c4091-126">보고서에 기본값을 가진 보고서 매개 변수가 포함되어 있고 `Prompt` 속성의 값이 `false`이면(즉, 보고서 관리자에서 사용자에게 확인 속성이 선택되지 않음) URL 내에서 해당 보고서 매개 변수에 대한 값을 전달할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c4091-126">If your report contains a report parameter that has a default value and the value of the `Prompt` property is `false` (that is, the Prompt User property is not selected in Report Manager), then you cannot pass a value for that report parameter within a URL.</span></span> <span data-ttu-id="c4091-127">이러한 기능을 통해 관리자는 최종 사용자가 특정 보고서 매개 변수의 값을 추가하거나 수정하지 못하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4091-127">This provides administrators an option for preventing end users from adding or modifying the values of certain report parameters.</span></span>  
  
##  <a name="additional-examples"></a><a name="bkmk_examples"></a> <span data-ttu-id="c4091-128">추가 예</span><span class="sxs-lookup"><span data-stu-id="c4091-128">Additional Examples</span></span>  
 <span data-ttu-id="c4091-129">다음 URL 예제에는 공백 및 여러 매개 변수가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="c4091-129">The following URL example includes spaces and multiple parameters</span></span>  
  
-   <span data-ttu-id="c4091-130">"SQL Server 사용자 교육 팀" 폴더 이름에는 공백이 포함되므로 "+"가 공백을 각각 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="c4091-130">Folder name of "SQL Server User Education Team" includes spaces and therefore the "+" replaces each space.</span></span>  
  
-   <span data-ttu-id="c4091-131">"팀 프로젝트 보고서" 보고서 이름에는 공백이 포함되므로 "+"가 공백을 각각 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="c4091-131">Report name of "team project report" includes spaces and therefore the "+" replaces each space.</span></span>  
  
-   <span data-ttu-id="c4091-132">두 개의 매개 변수 "teamgrouping2" 및 "teamgrouping1"에 값 "xgroup" 및 "ygroup"을 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="c4091-132">Passes two parameters of "teamgrouping2" with a value of "xgroup" and "teamgrouping1" with a value of "ygroup".</span></span>  
  
```  
https://myserver/Reportserver?/SQL+Server+User+Education+Team/_ContentTeams/folder123/team+project+report&teamgrouping2=xgroup&teamgrouping1=ygroup  
```  
  
 <span data-ttu-id="c4091-133">다음 URL 예제에는 다중 값 매개 변수 "OrderID"를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="c4091-133">The following URL example includes a multi-value parameter "OrderID.</span></span> <span data-ttu-id="c4091-134">다중 값 매개 변수의 형식은 각 값에 대해 매개 변수 이름을 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="c4091-134">The format for a Multi-Value parameter is to repeat the parameter name for each value.</span></span>  
  
```  
https://myserver/Reportserver?/SQL+Server+User+Education+Team/_ContentTeams/folder123/team+project+report&teamgrouping2=xgroup&teamgrouping1=ygroup&OrderID=747&OrderID=787&OrderID=12  
```  
  
 <span data-ttu-id="c4091-135">다음 URL 예제는 기본 모드 보고서 서버에 대해 값이 "7/1/2005" 인 *Sellsel의* 단일 매개 변수를 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4091-135">The following URL example passes a single parameter of *SellStartDate* with a value of "7/1/2005", for a native mode report server.</span></span>  
  
```  
http://myserver/ReportServer/Pages/ReportViewer.aspx?%2fProduct_and_Sales_Report_AdventureWorks&SellStartDate=7/1/2005  
```  
  
## <a name="see-also"></a><span data-ttu-id="c4091-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c4091-136">See Also</span></span>  
 <span data-ttu-id="c4091-137">[SSRS&#41;&#40;URL 액세스](url-access-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c4091-137">[URL Access &#40;SSRS&#41;](url-access-ssrs.md) </span></span>  
 [<span data-ttu-id="c4091-138">URL 액세스 매개 변수 참조</span><span class="sxs-lookup"><span data-stu-id="c4091-138">URL Access Parameter Reference</span></span>](url-access-parameter-reference.md)  
  
  
