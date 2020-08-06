---
title: GenerateDatabaseCreationScript 메서드 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- GenerateDatabaseCreationScript (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- GenerateDatabaseCreationScript method
ms.assetid: 25232dc7-00fe-4cd1-8a1c-7e36d552de00
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5e798aa25bec1cc478a6ec2cbdd0c21f44fa8215
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649915"
---
# <a name="generatedatabasecreationscript-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="85309-102">GenerateDatabaseCreationScript 메서드(WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="85309-102">GenerateDatabaseCreationScript Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="85309-103">보고서 서버 데이터베이스를 만드는 데 사용할 수 있는 SQL 스크립트를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="85309-103">Generates a SQL Script that can be used to create a report server database.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85309-104">구문</span><span class="sxs-lookup"><span data-stu-id="85309-104">Syntax</span></span>  
  
```vb  
Public Sub GenerateDatabaseCreationScript(ByVal DatabaseName As String, _  
    ByVal Lcid As Int32, ByVal IsSharePointMode As Boolean, ByRef Script As String, _  
    ByRef HRESULT As Int32)  
```  
  
```csharp  
public void GenerateDatabaseCreationScript(string DatabaseName, Int32 Lcid,   
    Boolean IsSharePointMode, out string Script, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="85309-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="85309-105">Parameters</span></span>  
 <span data-ttu-id="85309-106">*Databasename*</span><span class="sxs-lookup"><span data-stu-id="85309-106">*Databasename*</span></span>  
 <span data-ttu-id="85309-107">만들 보고서 서버 데이터베이스의 이름이 들어 있는 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="85309-107">A string containing the name of the report server database to create.</span></span>  
  
 <span data-ttu-id="85309-108">*Lcid*</span><span class="sxs-lookup"><span data-stu-id="85309-108">*Lcid*</span></span>  
 <span data-ttu-id="85309-109">역할 이름을 지역화하는 데 사용되는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="85309-109">Value used for localization of role names.</span></span>  
  
 <span data-ttu-id="85309-110">*IsSharePointMode*</span><span class="sxs-lookup"><span data-stu-id="85309-110">*IsSharePointMode*</span></span>  
 <span data-ttu-id="85309-111">데이터베이스를 기본 모드로 만들지, 아니면 SharePoint 모드로 만들지를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="85309-111">Indicates whether to create database in native mode or SharePoint mode.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="85309-112">부터 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] *IsSharePointMode* = `True` sharepoint 모드에서는가 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sharepoint 공유 서비스 이며 WMI 공급자에 의해 제어 되지 않으므로 IsSharePointMode은 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="85309-112">Beginning in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], *IsSharePointMode*=`True` is not supported because in SharePoint mode, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is a SharePoint shared service and is not controlled by the WMI provider.</span></span> <span data-ttu-id="85309-113">항상 이 매개 변수를 `False`로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="85309-113">You should always set this parameter to `False`.</span></span>  
  
 <span data-ttu-id="85309-114">*스크립트*</span><span class="sxs-lookup"><span data-stu-id="85309-114">*Script*</span></span>  
 <span data-ttu-id="85309-115">[out] 생성된 SQL 스크립트가 들어 있는 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="85309-115">[out] A string containing the generated SQL script.</span></span>  
  
 <span data-ttu-id="85309-116">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="85309-116">*HRESULT*</span></span>  
 <span data-ttu-id="85309-117">[out] 호출의 성공 여부를 나타내는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="85309-117">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="85309-118">Return Value</span><span class="sxs-lookup"><span data-stu-id="85309-118">Return Value</span></span>  
 <span data-ttu-id="85309-119">메서드 호출의 성공 또는 실패를 나타내는 *HRESULT* 를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="85309-119">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="85309-120">0 값은 메서드 호출이 성공했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="85309-120">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="85309-121">0 이외의 값은 오류가 발생했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="85309-121">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="85309-122">설명</span><span class="sxs-lookup"><span data-stu-id="85309-122">Remarks</span></span>  
 <span data-ttu-id="85309-123">이 메서드는 현재 연결되어 있는 보고서 서버 버전에 대한 보고서 서버 데이터베이스를 만드는 SQL 스크립트를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="85309-123">This method generates an SQL script that creates report server databases for the version of the report server currently connected to.</span></span>  
  
 <span data-ttu-id="85309-124">*DatabaseName* 매개 변수에 제공되는 값은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스 명명 규칙을 따라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="85309-124">The value supplied in the *DatabaseName* parameter must conform to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database naming conventions.</span></span>  
  
 <span data-ttu-id="85309-125">이 메서드는 스크립트를 생성할 때 데이터베이스가 있는지 확인하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="85309-125">The method does not check the existence of the database when generating the script.</span></span>  
  
 <span data-ttu-id="85309-126">이 메서드는 스크립트를 생성할 때 보고서 서버 데이터베이스가 있는지 확인하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="85309-126">This method does not check for the existence of the report server database when generating the script.</span></span>  
  
 <span data-ttu-id="85309-127">생성된 스크립트는 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005 및 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]을(를) 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="85309-127">The generated script supports [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005, and [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85309-128">요구 사항</span><span class="sxs-lookup"><span data-stu-id="85309-128">Requirements</span></span>  
 <span data-ttu-id="85309-129">**네임스페이스:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85309-129">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85309-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="85309-130">See Also</span></span>  
 [<span data-ttu-id="85309-131">MSReportServer_ConfigurationSetting 멤버</span><span class="sxs-lookup"><span data-stu-id="85309-131">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
