---
title: GetDatabaseVersionDisplayName 메서드(WMI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- GetDatabaseVersionDisplayName method
ms.assetid: e1286424-7043-4f12-a7ad-1cf69e81baa4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8b39ce39a4f26964c148631c903869b0234e2b9f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649910"
---
# <a name="getdatabaseversiondisplayname-method-wmi"></a><span data-ttu-id="4adaa-102">GetDatabaseVersionDisplayName 메서드(WMI)</span><span class="sxs-lookup"><span data-stu-id="4adaa-102">GetDatabaseVersionDisplayName Method (WMI)</span></span>
  <span data-ttu-id="4adaa-103">지정된 보고서 서버 데이터베이스 버전 문자열의 표시 이름을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="4adaa-103">Gets the display name for a given report server database version string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4adaa-104">구문</span><span class="sxs-lookup"><span data-stu-id="4adaa-104">Syntax</span></span>  
  
```vb  
Public Sub GetDatabaseVersionDisplayName(Version As String, DisplayName As String, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void GetDatabaseVersionDisplayName(string Version, string DisplayName, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4adaa-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="4adaa-105">Parameters</span></span>  
 <span data-ttu-id="4adaa-106">*버전*</span><span class="sxs-lookup"><span data-stu-id="4adaa-106">*Version*</span></span>  
 <span data-ttu-id="4adaa-107">보고서 서버 데이터베이스의 버전 문자열이 들어 있는 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="4adaa-107">A string that contains the version string for a report server database.</span></span>  
  
 <span data-ttu-id="4adaa-108">*DisplayName*</span><span class="sxs-lookup"><span data-stu-id="4adaa-108">*DisplayName*</span></span>  
 <span data-ttu-id="4adaa-109">[out] 제공된 버전에 해당하는 표시 이름이 들어 있는 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="4adaa-109">[out] A string that contains the display name that corresponds to the version supplied.</span></span>  
  
 <span data-ttu-id="4adaa-110">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="4adaa-110">*HRESULT*</span></span>  
 <span data-ttu-id="4adaa-111">[out] 호출의 성공 여부를 나타내는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="4adaa-111">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4adaa-112">설명</span><span class="sxs-lookup"><span data-stu-id="4adaa-112">Remarks</span></span>  
 <span data-ttu-id="4adaa-113">다음 표에서는 표시 문자열에 대한 데이터베이스 버전의 매핑을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4adaa-113">The following table shows the mapping from database version to display string.</span></span>  
  
|<span data-ttu-id="4adaa-114">**릴리스**</span><span class="sxs-lookup"><span data-stu-id="4adaa-114">**Release**</span></span>|`Version`|<span data-ttu-id="4adaa-115">**표시 이름**</span><span class="sxs-lookup"><span data-stu-id="4adaa-115">**Display Name**</span></span>|  
|-----------------|-----------------|----------------------|  
|<span data-ttu-id="4adaa-116">RS 2005 SP2</span><span class="sxs-lookup"><span data-stu-id="4adaa-116">RS 2005 SP2</span></span>|<span data-ttu-id="4adaa-117">@DBVersion = 'C.0.8.54'</span><span class="sxs-lookup"><span data-stu-id="4adaa-117">@DBVersion = 'C.0.8.54'</span></span>|<span data-ttu-id="4adaa-118">SQL Server 2005 SP2</span><span class="sxs-lookup"><span data-stu-id="4adaa-118">SQL Server 2005 SP2</span></span>|  
|<span data-ttu-id="4adaa-119">RS 2005 SP1</span><span class="sxs-lookup"><span data-stu-id="4adaa-119">RS 2005 SP1</span></span>|<span data-ttu-id="4adaa-120">@DBVersion = 'C.0.8.43'</span><span class="sxs-lookup"><span data-stu-id="4adaa-120">@DBVersion = 'C.0.8.43'</span></span>|<span data-ttu-id="4adaa-121">SQL Server 2005 SP1</span><span class="sxs-lookup"><span data-stu-id="4adaa-121">SQL Server 2005 SP1</span></span>|  
|<span data-ttu-id="4adaa-122">RS 2005 RTM</span><span class="sxs-lookup"><span data-stu-id="4adaa-122">RS 2005 RTM</span></span>|<span data-ttu-id="4adaa-123">@DBVersion = 'C.0.8.40'</span><span class="sxs-lookup"><span data-stu-id="4adaa-123">@DBVersion = 'C.0.8.40'</span></span>|<span data-ttu-id="4adaa-124">SQL Server 2005</span><span class="sxs-lookup"><span data-stu-id="4adaa-124">SQL Server 2005</span></span>|  
|<span data-ttu-id="4adaa-125">RS 2000 SP2</span><span class="sxs-lookup"><span data-stu-id="4adaa-125">RS 2000 SP2</span></span>|<span data-ttu-id="4adaa-126">@DBVersion = 'C.0.6.54'</span><span class="sxs-lookup"><span data-stu-id="4adaa-126">@DBVersion = 'C.0.6.54'</span></span>|<span data-ttu-id="4adaa-127">SQL Server 2000 SP2</span><span class="sxs-lookup"><span data-stu-id="4adaa-127">SQL Server 2000 SP2</span></span>|  
|<span data-ttu-id="4adaa-128">RS 2000 SP1</span><span class="sxs-lookup"><span data-stu-id="4adaa-128">RS 2000 SP1</span></span>|<span data-ttu-id="4adaa-129">@DBVersion = 'C.0.6.51'</span><span class="sxs-lookup"><span data-stu-id="4adaa-129">@DBVersion = 'C.0.6.51'</span></span>|<span data-ttu-id="4adaa-130">SQL Server 2000 SP1</span><span class="sxs-lookup"><span data-stu-id="4adaa-130">SQL Server 2000 SP1</span></span>|  
|<span data-ttu-id="4adaa-131">RS 2000 RTM</span><span class="sxs-lookup"><span data-stu-id="4adaa-131">RS 2000 RTM</span></span>|<span data-ttu-id="4adaa-132">@DBVersion = 'C.0.6.43'</span><span class="sxs-lookup"><span data-stu-id="4adaa-132">@DBVersion = 'C.0.6.43'</span></span>|<span data-ttu-id="4adaa-133">SQL Server 2000</span><span class="sxs-lookup"><span data-stu-id="4adaa-133">SQL Server 2000</span></span>|  
|<span data-ttu-id="4adaa-134">핫픽스</span><span class="sxs-lookup"><span data-stu-id="4adaa-134">Hotfix</span></span>||<span data-ttu-id="4adaa-135">적용 가능한 가장 가까운 버전</span><span class="sxs-lookup"><span data-stu-id="4adaa-135">Closest applicable version</span></span>|  
  
 <span data-ttu-id="4adaa-136">*2000 이전* 버전 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 경우 ACT_E_BAD_VERSION의 HRESULT가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="4adaa-136">For a *Version* prior to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2000 an HRESULT of ACT_E_BAD_VERSION is returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4adaa-137">Return Value</span><span class="sxs-lookup"><span data-stu-id="4adaa-137">Return Value</span></span>  
 <span data-ttu-id="4adaa-138">메서드 호출의 성공 또는 실패를 나타내는 *HRESULT* 를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="4adaa-138">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="4adaa-139">0 값은 메서드 호출이 성공했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4adaa-139">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="4adaa-140">0 이외의 값은 오류가 발생했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4adaa-140">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4adaa-141">요구 사항</span><span class="sxs-lookup"><span data-stu-id="4adaa-141">Requirements</span></span>  
 <span data-ttu-id="4adaa-142">**네임스페이스:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4adaa-142">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4adaa-143">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4adaa-143">See Also</span></span>  
 [<span data-ttu-id="4adaa-144">MSReportServer_ConfigurationSetting 멤버</span><span class="sxs-lookup"><span data-stu-id="4adaa-144">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
