---
title: GetReportServerUrls 메서드(WMI MSReportServer_Instance) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- GetReportServerUrls method
ms.assetid: 4865e32c-0114-465a-be8c-be223a7bc09e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f36a5ba10c05276cffabc155e5289d675db8dae7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733523"
---
# <a name="getreportserverurls-method-wmi-msreportserver_instance"></a><span data-ttu-id="1e9c5-102">GetReportServerUrls 메서드(WMI MSReportServer_Instance)</span><span class="sxs-lookup"><span data-stu-id="1e9c5-102">GetReportServerUrls Method (WMI MSReportServer_Instance)</span></span>
  <span data-ttu-id="1e9c5-103">사용자가 보고서 서버 및 보고서 관리자에 액세스하는 데 사용할 수 있는 URL 목록을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="1e9c5-103">Returns a list of URLs users can use to access the report server and report manager.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e9c5-104">구문</span><span class="sxs-lookup"><span data-stu-id="1e9c5-104">Syntax</span></span>  
  
```vb  
Public Sub GetReportServerUrls (ByRef ApplicationName() As String, ByRef URLs()_  
    As String, ByRef Length As Int32, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void GetReportServerUrls(out string[] applicationName,   
    out string[] URLs, out int length, out int HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1e9c5-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="1e9c5-105">Parameters</span></span>  
 <span data-ttu-id="1e9c5-106">*ApplicationName[]*</span><span class="sxs-lookup"><span data-stu-id="1e9c5-106">*ApplicationName[]*</span></span>  
 <span data-ttu-id="1e9c5-107">설치된 애플리케이션이 들어 있는 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="1e9c5-107">An array that contains the applications that are installed.</span></span> <span data-ttu-id="1e9c5-108">값은 `ReportServerWebService` 또는 `ReportManager`입니다.</span><span class="sxs-lookup"><span data-stu-id="1e9c5-108">Values are either `ReportServerWebService` or `ReportManager`.</span></span>  
  
 <span data-ttu-id="1e9c5-109">*URLs[]*</span><span class="sxs-lookup"><span data-stu-id="1e9c5-109">*URLs[]*</span></span>  
 <span data-ttu-id="1e9c5-110">성공적으로 등록된 URL이 들어 있는 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="1e9c5-110">An array that contains the successfully registered Urls.</span></span>  
  
 <span data-ttu-id="1e9c5-111">*길이*</span><span class="sxs-lookup"><span data-stu-id="1e9c5-111">*Length*</span></span>  
 <span data-ttu-id="1e9c5-112">반환된 배열의 길이가 들어 있는 정수 값입니다.</span><span class="sxs-lookup"><span data-stu-id="1e9c5-112">An integer value that contains the length of the arrays returned.</span></span>  
  
 <span data-ttu-id="1e9c5-113">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="1e9c5-113">*HRESULT*</span></span>  
 <span data-ttu-id="1e9c5-114">성공 또는 오류 코드를 나타내는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="1e9c5-114">A value that indicates success or an error code.</span></span>  
  
## <a name="return-values"></a><span data-ttu-id="1e9c5-115">반환 값</span><span class="sxs-lookup"><span data-stu-id="1e9c5-115">Return Values</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1e9c5-116">설명</span><span class="sxs-lookup"><span data-stu-id="1e9c5-116">Remarks</span></span>  
 <span data-ttu-id="1e9c5-117">WMI 관리 개체에서 노출되는 메서드는 InvokeMethod 함수를 통해 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e9c5-117">Methods exposed by WMI management objects are called through the InvokeMethod function.</span></span> <span data-ttu-id="1e9c5-118">자세한 내용은 [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework WMI 설명서의 "관리 개체에서 메서드 실행(Executing Methods on Management Objects)"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="1e9c5-118">For more information, please see "Executing Methods on Management Objects" in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework WMI documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e9c5-119">요구 사항</span><span class="sxs-lookup"><span data-stu-id="1e9c5-119">Requirements</span></span>  
 <span data-ttu-id="1e9c5-120">**네임스페이스:** [!INCLUDE[ssRSWMInmspc](../../includes/ssrswminmspc-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e9c5-120">**Namespace:** [!INCLUDE[ssRSWMInmspc](../../includes/ssrswminmspc-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e9c5-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1e9c5-121">See Also</span></span>  
 [<span data-ttu-id="1e9c5-122">MSReportServer_ConfigurationSetting 멤버</span><span class="sxs-lookup"><span data-stu-id="1e9c5-122">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
