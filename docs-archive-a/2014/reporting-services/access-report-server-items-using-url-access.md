---
title: URL 액세스를 사용하여 보고서 서버 항목 액세스 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- referencing URL items for report server access
- URL access [Reporting Services], report servers
ms.assetid: a58b4ca6-129d-45e9-95c7-e9169fe5bba4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6693419490c1b3770ccb41b2645cbdba8996630a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652664"
---
# <a name="access-report-server-items-using-url-access"></a><span data-ttu-id="ba616-102">URL 액세스를 사용하여 보고서 서버 항목 액세스</span><span class="sxs-lookup"><span data-stu-id="ba616-102">Access Report Server Items Using URL Access</span></span>
  <span data-ttu-id="ba616-103">이 항목에서는 *rs:Command*=*Value*를 사용하여 보고서 서버 데이터베이스 또는 SharePoint 사이트에서 여러 형식의 카탈로그 항목에 액세스하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ba616-103">This topic describes how to access catalog items of different types in a report server data base or in a SharePoint site using *rs:Command*=*Value*.</span></span>  
  
 <span data-ttu-id="ba616-104">이 매개 변수 문자열을  추가할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ba616-104">It is not necessary to add this parameter string.</span></span> <span data-ttu-id="ba616-105">이 문자열을 생략한 경우 보고서 서버에서 항목 형식을 평가하고 알맞은 매개 변수 값을 자동으로 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ba616-105">If you omit it, the report server evaluates the item type and selects the appropriate parameter value automatically.</span></span> <span data-ttu-id="ba616-106">그러나 URL에서 *rs:Command*=*Value* 문자열을 사용하면 보고서 서버의 성능이 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="ba616-106">However, using the *rs:Command*=*Value* string in the URL improves the performance of the report server.</span></span>  
  
 <span data-ttu-id="ba616-107">아래 예의 `_vti_bin` 프록시 구문을 참고하십시오.</span><span class="sxs-lookup"><span data-stu-id="ba616-107">Note the `_vti_bin` proxy syntax in the examples below.</span></span> <span data-ttu-id="ba616-108">프록시 구문을 사용하는 방법에 대한 자세한 내용은 [URL Access Parameter Reference](url-access-parameter-reference.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ba616-108">For more information about using the proxy syntax, see [URL Access Parameter Reference](url-access-parameter-reference.md).</span></span>  
  
## <a name="access-a-report"></a><span data-ttu-id="ba616-109">보고서 액세스</span><span class="sxs-lookup"><span data-stu-id="ba616-109">Access a Report</span></span>  
 <span data-ttu-id="ba616-110">브라우저에서 보고서를 보려면 *rs: Command* = *Render* 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ba616-110">To view a report in the browser, use the *rs:Command*=*Render* parameter.</span></span> <span data-ttu-id="ba616-111">예를 들어:</span><span class="sxs-lookup"><span data-stu-id="ba616-111">For example:</span></span>  
  
 <span data-ttu-id="ba616-112">`Native` `http://myrshost/reportserver?/Sales/YearlySalesByCategory&rs:Command=Render`</span><span class="sxs-lookup"><span data-stu-id="ba616-112">`Native` `http://myrshost/reportserver?/Sales/YearlySalesByCategory&rs:Command=Render`</span></span>  
  
 <span data-ttu-id="ba616-113">`SharePoint` `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales/YearlySalesByCategory&rs:Command=Render`</span><span class="sxs-lookup"><span data-stu-id="ba616-113">`SharePoint` `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales/YearlySalesByCategory&rs:Command=Render`</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="ba616-114">URL에는 SharePoint를 통해 요청을 라우팅하는 `_vti_bin` 프록시 구문과 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] HTTP 프록시를 포함하는 것이 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="ba616-114">It is important the URL include the `_vti_bin` proxy syntax to route the request through SharePoint and the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] HTTP proxy.</span></span> <span data-ttu-id="ba616-115">프록시는 몇 가지 컨텍스트를 HTTP 요청에 추가하며 이 컨텍스트는 SharePoint 모드 보고서 서버에 대한 보고서의 올바른 실행을 보장하는 데 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="ba616-115">The proxy adds some context to the HTTP request, context that is required to ensure proper execution of the report for SharePoint mode report servers.</span></span>  
  
## <a name="access-a-resource"></a><span data-ttu-id="ba616-116">리소스 액세스</span><span class="sxs-lookup"><span data-stu-id="ba616-116">Access a Resource</span></span>  
 <span data-ttu-id="ba616-117">리소스에 액세스 하려면 *rs: Command* = *GetResourceContents* 매개 변수를 사용 합니다. 리소스가 이미지와 같은 브라우저와 호환 되는 경우 브라우저에서 열립니다.</span><span class="sxs-lookup"><span data-stu-id="ba616-117">To access a resource, use the *rs:Command*=*GetResourceContents* parameter.If the resource is compatible with the browser, such as an image, it is opened in the browser.</span></span> <span data-ttu-id="ba616-118">그렇지 않으면 파일 또는 리소스를 열거나 디스크에 저장하라는 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="ba616-118">Otherwise, you are prompted to open or save the file or resource to disk.</span></span>  
  
 <span data-ttu-id="ba616-119">`Native` `http://myrshost/reportserver?/Sales/StorePicture&rs:Command=GetResourceContents`</span><span class="sxs-lookup"><span data-stu-id="ba616-119">`Native` `http://myrshost/reportserver?/Sales/StorePicture&rs:Command=GetResourceContents`</span></span>  
  
 <span data-ttu-id="ba616-120">`SharePoint` `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales/StorePicture.jpg&rs:Command=GetResourceContents`</span><span class="sxs-lookup"><span data-stu-id="ba616-120">`SharePoint` `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales/StorePicture.jpg&rs:Command=GetResourceContents`</span></span>  
  
## <a name="access-a-data-source"></a><span data-ttu-id="ba616-121">데이터 원본 액세스</span><span class="sxs-lookup"><span data-stu-id="ba616-121">Access a Data Source</span></span>  
 <span data-ttu-id="ba616-122">데이터 원본에 액세스 하려면 *rs: Command* = *GetDataSourceContents* 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ba616-122">To access a data source, use the *rs:Command*=*GetDataSourceContents* parameter.</span></span> <span data-ttu-id="ba616-123">브라우저에서 XML을 지원하는 경우 데이터 원본에 대해 `Read Contents` 권한을 가진 인증된 사용자이면 데이터 원본 정의가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ba616-123">If your browser supports XML, the data source definition is displayed if you are an authenticated user with `Read Contents` permission on the data source.</span></span> <span data-ttu-id="ba616-124">예를 들어:</span><span class="sxs-lookup"><span data-stu-id="ba616-124">For example:</span></span>  
  
 <span data-ttu-id="ba616-125">`Native` `http://myrshost/reportserver?/Sales/AdventureWorks2012&rs:Command=GetDataSourceContents`</span><span class="sxs-lookup"><span data-stu-id="ba616-125">`Native` `http://myrshost/reportserver?/Sales/AdventureWorks2012&rs:Command=GetDataSourceContents`</span></span>  
  
 <span data-ttu-id="ba616-126">`SharePoint` `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales/AdventureWorks2012&rs:Command=GetDataSourceContents`</span><span class="sxs-lookup"><span data-stu-id="ba616-126">`SharePoint` `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales/AdventureWorks2012&rs:Command=GetDataSourceContents`</span></span>  
  
 <span data-ttu-id="ba616-127">XML 구조는 다음 예와 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="ba616-127">The XML structure might look similar to the following example:</span></span>  
  
```  
<DataSourceDefinition>  
   <Extension>SQL</Extension>  
   <ConnectString>Provider=SQLOLEDB.1;Integrated Security=SSPI;Persist Security Info=False;Initial Catalog=AdventureWorks2012;Data Source=MYSERVER1;</ConnectString>  
   <CredentialRetrieval>Integrated</CredentialRetrieval>  
   <WindowsCredentials>False</WindowsCredentials>  
   <ImpersonateUser>False</ImpersonateUser>  
   <Prompt />  
   <Enabled>True</Enabled>  
</DataSourceDefinition>  
```  
  
 <span data-ttu-id="ba616-128">연결 문자열은 보고서 서버의 **SecureConnectionLevel** 설정을 기준으로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="ba616-128">The connection string is returned based on the **SecureConnectionLevel** setting of the report server.</span></span> <span data-ttu-id="ba616-129">**SecureConnectionLevel** 설정에 대한 자세한 내용은 [Using Secure Web Service Methods](report-server-web-service/net-framework/using-secure-web-service-methods.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ba616-129">For more information about the **SecureConnectionLevel** setting, see [Using Secure Web Service Methods](report-server-web-service/net-framework/using-secure-web-service-methods.md).</span></span>  
  
## <a name="access-the-contents-of-a-folder"></a><span data-ttu-id="ba616-130">폴더 내용 액세스</span><span class="sxs-lookup"><span data-stu-id="ba616-130">Access the Contents of a Folder</span></span>  
 <span data-ttu-id="ba616-131">폴더 내용에 액세스 하려면 *rs: Command* = *getchildren* 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ba616-131">To access the contents of a folder, use the *rs:Command*=*GetChildren* parameter.</span></span> <span data-ttu-id="ba616-132">요청된 폴더의 하위 폴더, 보고서, 데이터 원본 및 리소스에 대한 링크가 포함된 일반적인 폴더 탐색 페이지가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="ba616-132">A generic folder-navigation page is returned that contains links to the subfolders, reports, data sources, and resources in the requested folder.</span></span> <span data-ttu-id="ba616-133">예를 들어:</span><span class="sxs-lookup"><span data-stu-id="ba616-133">For example:</span></span>  
  
 <span data-ttu-id="ba616-134">`Native` `http://myrshost/reportserver?/Sales&rs:Command=GetChildren`</span><span class="sxs-lookup"><span data-stu-id="ba616-134">`Native` `http://myrshost/reportserver?/Sales&rs:Command=GetChildren`</span></span>  
  
 <span data-ttu-id="ba616-135">`SharePoint` `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales&rs:Command=GetChildren`</span><span class="sxs-lookup"><span data-stu-id="ba616-135">`SharePoint` `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales&rs:Command=GetChildren`</span></span>  
  
 <span data-ttu-id="ba616-136">표시되는 사용자 인터페이스는 [!INCLUDE[msCoName](../includes/msconame-md.md)] IIS(Internet Information Server)에서 사용되는 디렉터리 탐색 모드와 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="ba616-136">The user interface you see is similar to the directory browsing mode used by [!INCLUDE[msCoName](../includes/msconame-md.md)] Internet Information Server (IIS).</span></span> <span data-ttu-id="ba616-137">빌드 번호를 포함한 보고서 서버의 버전 번호도 폴더 목록 아래에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ba616-137">The version number, including the build number, of the report server is also displayed below the folder listing.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba616-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ba616-138">See Also</span></span>  
 <span data-ttu-id="ba616-139">[SSRS&#41;&#40;URL 액세스](url-access-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ba616-139">[URL Access &#40;SSRS&#41;](url-access-ssrs.md) </span></span>  
 [<span data-ttu-id="ba616-140">URL 액세스 매개 변수 참조</span><span class="sxs-lookup"><span data-stu-id="ba616-140">URL Access Parameter Reference</span></span>](url-access-parameter-reference.md)  
  
  
