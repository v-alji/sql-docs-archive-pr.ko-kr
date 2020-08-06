---
title: SetVirtualDirectory 메서드(WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- SetVirtualDirectory method
ms.assetid: 1a25cb1d-38d5-401a-970b-87b642a780e4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7f45181f3f6a791f5cb64a7519285b6d2a87dd36
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737696"
---
# <a name="setvirtualdirectory-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="e4494-102">SetVirtualDirectory 메서드(WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="e4494-102">SetVirtualDirectory Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="e4494-103">지정한 애플리케이션에 가상 디렉터리 이름을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e4494-103">Sets the name of the virtual directory for a given application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4494-104">구문</span><span class="sxs-lookup"><span data-stu-id="e4494-104">Syntax</span></span>  
  
```vb  
Public Sub SetVirtualDirectory(ByVal Application As String, _  
    ByVal VirtualDirectory As String, ByVal lcid As Int32, _  
    ByRef [Error] As String, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void SetVirtualDirectory(string Application, string VirtualDirectory,   
       int Lcid,out string Error, out int HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e4494-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="e4494-105">Parameters</span></span>  
 <span data-ttu-id="e4494-106">*애플리케이션*</span><span class="sxs-lookup"><span data-stu-id="e4494-106">*Application*</span></span>  
 <span data-ttu-id="e4494-107">가상 디렉터리를 설정할 애플리케이션의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="e4494-107">The name of application for which to set the virtual directory.</span></span>  
  
 <span data-ttu-id="e4494-108">*VirtualDirectory*</span><span class="sxs-lookup"><span data-stu-id="e4494-108">*VirtualDirectory*</span></span>  
 <span data-ttu-id="e4494-109">가상 디렉터리의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="e4494-109">The name of the virtual directory.</span></span>  
  
 <span data-ttu-id="e4494-110">*lcid*</span><span class="sxs-lookup"><span data-stu-id="e4494-110">*lcid*</span></span>  
 <span data-ttu-id="e4494-111">가상 디렉터리의 로캘 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="e4494-111">The locale id for the virtual directory.</span></span>  
  
 <span data-ttu-id="e4494-112">*오류*</span><span class="sxs-lookup"><span data-stu-id="e4494-112">*Error*</span></span>  
 <span data-ttu-id="e4494-113">[out] 발생한 오류에 대한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="e4494-113">[out] The description of the error that occurred.</span></span>  
  
 <span data-ttu-id="e4494-114">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="e4494-114">*HRESULT*</span></span>  
 <span data-ttu-id="e4494-115">[out] 호출의 성공 여부를 나타내는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="e4494-115">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e4494-116">Return Value</span><span class="sxs-lookup"><span data-stu-id="e4494-116">Return Value</span></span>  
 <span data-ttu-id="e4494-117">메서드 호출의 성공 또는 실패를 나타내는 *HRESULT* 를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="e4494-117">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="e4494-118">0 값은 메서드 호출이 성공했음을 나타내고 오류 코드는 호출이 실패했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e4494-118">A value of 0 indicates that the method call was successful; an error code indicates the call was not successful.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e4494-119">설명</span><span class="sxs-lookup"><span data-stu-id="e4494-119">Remarks</span></span>  
 <span data-ttu-id="e4494-120">각 애플리케이션의 모든 URL 예약에 대해 하나의 가상 디렉터리 이름만 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4494-120">An application can have only one virtual directory name for all URL reservations.</span></span>  
  
 <span data-ttu-id="e4494-121">VirtualDirectory는 가상 디렉터리의 명명 규칙을 준수해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4494-121">VirtualDirectory must conform to naming conventions for virtual directories.</span></span> <span data-ttu-id="e4494-122">VirtualDirectory는 빈 문자열이나 공백이 될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e4494-122">VirtualDirectory must not be empty string or blank.</span></span>  
  
 <span data-ttu-id="e4494-123">\Configuration\URLReservations\Application\VirtualDirectory 요소의 값을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="e4494-123">Updates the value of the \Configuration\URLReservations\Application\VirtualDirectory element.</span></span> <span data-ttu-id="e4494-124">URL 예약을 만들지 않아도 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4494-124">Succeeds even if no URL reservations have been created yet.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4494-125">요구 사항</span><span class="sxs-lookup"><span data-stu-id="e4494-125">Requirements</span></span>  
 <span data-ttu-id="e4494-126">**네임스페이스:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4494-126">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4494-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e4494-127">See Also</span></span>  
 [<span data-ttu-id="e4494-128">MSReportServer_ConfigurationSetting 멤버</span><span class="sxs-lookup"><span data-stu-id="e4494-128">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
