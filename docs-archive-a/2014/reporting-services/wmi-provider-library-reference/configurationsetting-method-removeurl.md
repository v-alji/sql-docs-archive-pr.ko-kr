---
title: RemoveURL 메서드(WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- RemoveURL method
ms.assetid: 3d98bd97-e152-48ce-ab1c-bd2c4f8b7fe9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3a32989e8ce8986b785e829d8cc7fcf58fbbf240
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652006"
---
# <a name="removeurl-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="d828f-102">RemoveURL 메서드(WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="d828f-102">RemoveURL Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="d828f-103">보고서 서버용으로 예약된 URL을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="d828f-103">Removes a URL reserved for the report server.</span></span> <span data-ttu-id="d828f-104">제거할 URL이 여러 개인 경우 이 API를 호출하여 하나씩 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d828f-104">If there are multiple URLs that need to be removed, this must be done one by one calling this API.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d828f-105">구문</span><span class="sxs-lookup"><span data-stu-id="d828f-105">Syntax</span></span>  
  
```vb  
Public Sub RemoveURL(ByVal Application As String, _  
    ByVal UrlString As String, ByVal Lcid As Int32, _  
    ByRef [Error] As String, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void RemoveURL(string Application, string UrlString, int Lcid,   
    out string Error, out int HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d828f-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="d828f-106">Parameters</span></span>  
 <span data-ttu-id="d828f-107">*애플리케이션*</span><span class="sxs-lookup"><span data-stu-id="d828f-107">*Application*</span></span>  
 <span data-ttu-id="d828f-108">예약을 제거할 애플리케이션의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="d828f-108">The name of application for which to remove the reservation.</span></span>  
  
 <span data-ttu-id="d828f-109">*URLString*</span><span class="sxs-lookup"><span data-stu-id="d828f-109">*URLString*</span></span>  
 <span data-ttu-id="d828f-110">예약에 대한 URL입니다.</span><span class="sxs-lookup"><span data-stu-id="d828f-110">The URL for the reservation.</span></span>  
  
 <span data-ttu-id="d828f-111">*lcid*</span><span class="sxs-lookup"><span data-stu-id="d828f-111">*lcid*</span></span>  
 <span data-ttu-id="d828f-112">반환되는 오류 메시지에 사용할 로캘입니다.</span><span class="sxs-lookup"><span data-stu-id="d828f-112">The locale to use for the error messages returned.</span></span>  
  
 <span data-ttu-id="d828f-113">*오류*</span><span class="sxs-lookup"><span data-stu-id="d828f-113">*Error*</span></span>  
 <span data-ttu-id="d828f-114">[out] 발생한 오류에 대한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="d828f-114">[out] The description of the error that occurred.</span></span>  
  
 <span data-ttu-id="d828f-115">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="d828f-115">*HRESULT*</span></span>  
 <span data-ttu-id="d828f-116">[out] 호출의 성공 여부를 나타내는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="d828f-116">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d828f-117">Return Value</span><span class="sxs-lookup"><span data-stu-id="d828f-117">Return Value</span></span>  
 <span data-ttu-id="d828f-118">메서드 호출의 성공 또는 실패를 나타내는 *HRESULT* 를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d828f-118">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="d828f-119">0 값은 메서드 호출이 성공했음을 나타내고 오류 코드는 호출이 실패했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d828f-119">A value of 0 indicates that the method call was successful; an error code indicates the call was not successful.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d828f-120">설명</span><span class="sxs-lookup"><span data-stu-id="d828f-120">Remarks</span></span>  
 <span data-ttu-id="d828f-121">*UrlString*에는 가상 디렉터리 이름이 포함되지 않습니다. 해당 용도로 [SetVirtualDirectory 메서드&#40;WMI MSReportServer_ConfigurationSetting&#41;](configurationsetting-method-setvirtualdirectory.md) 메서드가 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="d828f-121">*UrlString* does not include the Virtual Directory name - the [SetVirtualDirectory Method &#40;WMI MSReportServer_ConfigurationSetting&#41;](configurationsetting-method-setvirtualdirectory.md) method is provided for that purpose.</span></span>  
  
 <span data-ttu-id="d828f-122">[ReserveURL](configurationsetting-method-reserveurl.md) 메서드를 호출하기 전에 *Application* 매개 변수의 VirtualDirectory 구성 속성에 값을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d828f-122">Before calling the [ReserveURL](configurationsetting-method-reserveurl.md) method, you must supply a value for the VirtualDirectory configuration property for the *Application* parameter.</span></span> <span data-ttu-id="d828f-123">[SetVirtualDirectory 메서드&#40;WMI MSReportServer_ConfigurationSetting&#41;](configurationsetting-method-setvirtualdirectory.md) 메서드를 사용하여 VirtualDirectory 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d828f-123">Use the [SetVirtualDirectory Method &#40;WMI MSReportServer_ConfigurationSetting&#41;](configurationsetting-method-setvirtualdirectory.md) method to set the VirtualDirectory property.</span></span>  
  
 <span data-ttu-id="d828f-124">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 에서 제공한 SSL 인증서가 다른 URL에서 더 이상 사용되지 않을 경우 해당 인증서는 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="d828f-124">If an SSL Certificate was provisioned by [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] and no other URLs need it, it is removed.</span></span>  
  
 <span data-ttu-id="d828f-125">이 메서드를 사용하면 구성 응용 프로그램 도메인을 제외한 모든 응용 프로그램 도메인이 하드 재활용됩니다. 이 작업이 진행되는 동안 응용 프로그램 도메인이 중지되므로 이 작업이 완료되면 응용 프로그램 도메인을 다시 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d828f-125">This method causes all non-configuration app domains to hard recycle and stop during this operation; app domains are restarted after this operation complete.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d828f-126">요구 사항</span><span class="sxs-lookup"><span data-stu-id="d828f-126">Requirements</span></span>  
 <span data-ttu-id="d828f-127">**네임스페이스:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d828f-127">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d828f-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d828f-128">See Also</span></span>  
 [<span data-ttu-id="d828f-129">MSReportServer_ConfigurationSetting 멤버</span><span class="sxs-lookup"><span data-stu-id="d828f-129">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
