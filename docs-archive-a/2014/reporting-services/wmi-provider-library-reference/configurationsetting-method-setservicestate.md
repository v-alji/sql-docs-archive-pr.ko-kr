---
title: SetServiceState 메서드(WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- SetServiceState (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- SetServiceState method
ms.assetid: 9e1ee42d-b388-4929-89c7-8741b956c3be
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 70b4a29b3379fc1d312af42a1f5b1296ee35dcf3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737702"
---
# <a name="setservicestate-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="ef56c-102">SetServiceState 메서드(WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="ef56c-102">SetServiceState Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="ef56c-103">보고서 서버 Windows 및 웹 서비스를 설정하거나 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="ef56c-103">Turns the Report Server Windows and Web services on and off.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef56c-104">구문</span><span class="sxs-lookup"><span data-stu-id="ef56c-104">Syntax</span></span>  
  
```vb  
Public Sub SetServiceState(ByVal EnableWindowsService As Boolean, _  
    ByVal EnableWebService As Boolean, ByVal EnableReportManager As Boolean, _  
    ByRef HRESULT As Int32)  
```  
  
```csharp  
public void SetSecureConnectionLevel(Boolean EnableWindowsService,  
    Boolean EnableWebService, Boolean EnableReportManager, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ef56c-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="ef56c-105">Parameters</span></span>  
 <span data-ttu-id="ef56c-106">*EnableWindowsService*</span><span class="sxs-lookup"><span data-stu-id="ef56c-106">*EnableWindowsService*</span></span>  
 <span data-ttu-id="ef56c-107">Windows 서비스의 상태를 나타내는 `Boolean` 값입니다.</span><span class="sxs-lookup"><span data-stu-id="ef56c-107">A `Boolean` value indicating the state of the Windows service.</span></span> <span data-ttu-id="ef56c-108">`true` 값은 보고서 서버 Windows 서비스를 시작하고 `false` 값은 Windows 서비스를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="ef56c-108">A value of `true` starts the Report Server Windows service; a value of `false` stops the Windows service.</span></span>  
  
 <span data-ttu-id="ef56c-109">*EnableWebService*</span><span class="sxs-lookup"><span data-stu-id="ef56c-109">*EnableWebService*</span></span>  
 <span data-ttu-id="ef56c-110">`Boolean`웹 서비스의 상태를 나타내는 값 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 입니다.</span><span class="sxs-lookup"><span data-stu-id="ef56c-110">A `Boolean` value indicating the state of the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Web service.</span></span> <span data-ttu-id="ef56c-111">`true` 값은 보고서 서버 웹 서비스를 시작하고 `false` 값은 웹 서비스를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="ef56c-111">A value of `true` starts the Report Server Web service; a value of `false` stops the Web service</span></span>  
  
 <span data-ttu-id="ef56c-112">*EnableReportManager*</span><span class="sxs-lookup"><span data-stu-id="ef56c-112">*EnableReportManager*</span></span>  
 <span data-ttu-id="ef56c-113">보고서 관리자의 필요한 상태를 나타내는 `Boolean` 값입니다.</span><span class="sxs-lookup"><span data-stu-id="ef56c-113">A `Boolean` value indicating the desired state of the Report manager.</span></span>  
  
 <span data-ttu-id="ef56c-114">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="ef56c-114">*HRESULT*</span></span>  
 <span data-ttu-id="ef56c-115">[out] 호출의 성공 여부를 나타내는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="ef56c-115">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ef56c-116">Return Value</span><span class="sxs-lookup"><span data-stu-id="ef56c-116">Return Value</span></span>  
 <span data-ttu-id="ef56c-117">메서드 호출의 성공 또는 실패를 나타내는 *HRESULT* 를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ef56c-117">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="ef56c-118">0 값은 메서드 호출이 성공했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ef56c-118">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="ef56c-119">0 이외의 값은 오류가 발생했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ef56c-119">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ef56c-120">설명</span><span class="sxs-lookup"><span data-stu-id="ef56c-120">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef56c-121">요구 사항</span><span class="sxs-lookup"><span data-stu-id="ef56c-121">Requirements</span></span>  
 <span data-ttu-id="ef56c-122">**네임스페이스:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef56c-122">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef56c-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ef56c-123">See Also</span></span>  
 [<span data-ttu-id="ef56c-124">MSReportServer_ConfigurationSetting 멤버</span><span class="sxs-lookup"><span data-stu-id="ef56c-124">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
