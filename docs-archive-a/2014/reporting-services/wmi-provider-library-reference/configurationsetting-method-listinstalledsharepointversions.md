---
title: ListInstalledSharePointVersions 메서드(WMI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- ListInstalledSharePointVersions method
ms.assetid: 8f0a5e9f-23f1-41e5-9a90-dfec19ef1df7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f0ceee23876461cf31cbd265ea39ae015ddcbc49
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649909"
---
# <a name="listinstalledsharepointversions-method-wmi"></a><span data-ttu-id="d5790-102">ListInstalledSharePointVersions 메서드(WMI)</span><span class="sxs-lookup"><span data-stu-id="d5790-102">ListInstalledSharePointVersions Method (WMI)</span></span>
  <span data-ttu-id="d5790-103">보고서 서버와 같은 컴퓨터에 설치되어 있는 Microsoft [!INCLUDE[winSPServ](../../includes/winspserv-md.md)], [!INCLUDE[offSPServ](../../includes/offspserv-md.md)], [!INCLUDE[SPF2010](../../includes/spf2010-md.md)]또는 [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] 버전을 나타내는 토큰 집합을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d5790-103">Returns a set of tokens that represent the versions of Microsoft [!INCLUDE[winSPServ](../../includes/winspserv-md.md)], [!INCLUDE[offSPServ](../../includes/offspserv-md.md)], [!INCLUDE[SPF2010](../../includes/spf2010-md.md)], or [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] that are installed on the same computer as the report server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5790-104">구문</span><span class="sxs-lookup"><span data-stu-id="d5790-104">Syntax</span></span>  
  
```vb  
Public Sub ListInstalledSharePointVersions(ByRef VersionTokens() _  
    As String, ByRef Length As Int32, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void ListReportServersInDatabase (out string[] VersionTokens,   
    out Int32 Length, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d5790-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="d5790-105">Parameters</span></span>  
 <span data-ttu-id="d5790-106">*VersionTokens[]*</span><span class="sxs-lookup"><span data-stu-id="d5790-106">*VersionTokens[]*</span></span>  
 <span data-ttu-id="d5790-107">[out] 설치된 보고서 서버와 호환되는 SharePoint 제품 또는 기술의 버전을 나타내는 토큰이 들어 있는 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="d5790-107">[out] An array that contains the tokens that represent the version of a SharePoint product or technology that is compatible with the installed report server.</span></span>  
  
 <span data-ttu-id="d5790-108">*길이*</span><span class="sxs-lookup"><span data-stu-id="d5790-108">*Length*</span></span>  
 <span data-ttu-id="d5790-109">[out] 버전 토큰 배열의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="d5790-109">[out] The length of the version tokens array.</span></span>  
  
 <span data-ttu-id="d5790-110">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="d5790-110">*HRESULT*</span></span>  
 <span data-ttu-id="d5790-111">[out] 호출의 성공 여부를 나타내는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="d5790-111">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d5790-112">Return Value</span><span class="sxs-lookup"><span data-stu-id="d5790-112">Return Value</span></span>  
 <span data-ttu-id="d5790-113">메서드 호출의 성공 또는 실패를 나타내는 *HRESULT* 를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d5790-113">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="d5790-114">0 값은 메서드 호출이 성공했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d5790-114">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="d5790-115">0 이외의 값은 오류가 발생했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d5790-115">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d5790-116">설명</span><span class="sxs-lookup"><span data-stu-id="d5790-116">Remarks</span></span>  
 <span data-ttu-id="d5790-117">반환되는 각 토큰은 현재 설치되어 있는 보고서 서버와 호환되는 [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] 또는 [!INCLUDE[SPF2010](../../includes/spf2010-md.md)] 버전을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d5790-117">Each token that is returned represents a version of [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] or [!INCLUDE[SPF2010](../../includes/spf2010-md.md)] that is compatible with the currently installed report server.</span></span> <span data-ttu-id="d5790-118">특정 버전의 SharePoint가 이전 SharePoint 버전과 호환되는 경우 호환되는 각 SharePoint 버전에 대한 토큰이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="d5790-118">If a particular version of SharePoint is compatible with previous SharePoint versions, tokens for each compatible SharePoint version are returned.</span></span>  
  
 <span data-ttu-id="d5790-119">다음 표에서는 반환되는 SharePoint 토큰을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d5790-119">The following is a table of the SharePoint tokens that are returned.</span></span>  
  
|<span data-ttu-id="d5790-120">**버전 토큰**</span><span class="sxs-lookup"><span data-stu-id="d5790-120">**Version Tokens**</span></span>|<span data-ttu-id="d5790-121">**설명**</span><span class="sxs-lookup"><span data-stu-id="d5790-121">**Description**</span></span>|  
|------------------------|---------------------|  
|<span data-ttu-id="d5790-122">WSS_V2_Compatible</span><span class="sxs-lookup"><span data-stu-id="d5790-122">WSS_V2_Compatible</span></span>|<span data-ttu-id="d5790-123">[!INCLUDE[winSPServ](../../includes/winspserv-md.md)]2.0과 호환되는 [!INCLUDE[winSPServ](../../includes/winspserv-md.md)], [!INCLUDE[offSPServ](../../includes/offspserv-md.md)], [!INCLUDE[SPF2010](../../includes/spf2010-md.md)], [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] 또는 [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] 설치 프로그램이 설치되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5790-123">A [!INCLUDE[winSPServ](../../includes/winspserv-md.md)], [!INCLUDE[winSPServ](../../includes/winspserv-md.md)], [!INCLUDE[offSPServ](../../includes/offspserv-md.md)], [!INCLUDE[SPF2010](../../includes/spf2010-md.md)], or [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] installation is installed that is compatible with [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] 2.0.</span></span>|  
|<span data-ttu-id="d5790-124">WSS_V3_Compatible</span><span class="sxs-lookup"><span data-stu-id="d5790-124">WSS_V3_Compatible</span></span>|<span data-ttu-id="d5790-125">[!INCLUDE[winSPServ](../../includes/winspserv-md.md)]3.0과 호환되는 [!INCLUDE[winSPServ](../../includes/winspserv-md.md)], [!INCLUDE[offSPServ](../../includes/offspserv-md.md)], [!INCLUDE[SPF2010](../../includes/spf2010-md.md)], [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] 또는 [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] 이 설치되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5790-125">A [!INCLUDE[winSPServ](../../includes/winspserv-md.md)], [!INCLUDE[winSPServ](../../includes/winspserv-md.md)], [!INCLUDE[offSPServ](../../includes/offspserv-md.md)], [!INCLUDE[SPF2010](../../includes/spf2010-md.md)], or [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] installation is installed that is compatible with [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] 3.0.</span></span>|  
|<span data-ttu-id="d5790-126">WSS_V4_Compatible</span><span class="sxs-lookup"><span data-stu-id="d5790-126">WSS_V4_Compatible</span></span>|<span data-ttu-id="d5790-127">Office 14와 호환되는 [!INCLUDE[SPF2010](../../includes/spf2010-md.md)] 또는 [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] 이 설치되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5790-127">A [!INCLUDE[SPF2010](../../includes/spf2010-md.md)] or [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] installation is installed that is compatible with Office 14.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d5790-128">요구 사항</span><span class="sxs-lookup"><span data-stu-id="d5790-128">Requirements</span></span>  
 <span data-ttu-id="d5790-129">**네임스페이스:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5790-129">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5790-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d5790-130">See Also</span></span>  
 [<span data-ttu-id="d5790-131">MSReportServer_ConfigurationSetting 멤버</span><span class="sxs-lookup"><span data-stu-id="d5790-131">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
