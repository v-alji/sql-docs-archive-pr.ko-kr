---
title: DatabaseLogonType 속성(WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- DatabaseLogonType
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- DatabaseLogonType property
ms.assetid: 6b592582-4c35-4029-ab86-982fff47d8d6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3bb5a4149c29fb7532b7140a2616dd856e6db2b5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737665"
---
# <a name="databaselogontype-property-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="ea32e-102">DatabaseLogonType 속성(WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="ea32e-102">DatabaseLogonType Property (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="ea32e-103">보고서 서버가 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 서비스 계정, Windows 사용자 계정 또는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인을 사용하여 보고서 서버 데이터베이스에 액세스하는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ea32e-103">Specifies whether the report server uses a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows service account, a Windows user account, or a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login to access the report server database.</span></span> <span data-ttu-id="ea32e-104">읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="ea32e-104">Read-only.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea32e-105">구문</span><span class="sxs-lookup"><span data-stu-id="ea32e-105">Syntax</span></span>  
  
```vb  
Public Dim DatabaseLogonType As Integer  
```  
  
```csharp  
public int DatabaseLogonType;  
```  
  
## <a name="property-values"></a><span data-ttu-id="ea32e-106">속성 값</span><span class="sxs-lookup"><span data-stu-id="ea32e-106">Property Values</span></span>  
 <span data-ttu-id="ea32e-107">로그인 유형을 나타내는 `integer` 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="ea32e-107">An `integer` object that represents the login type.</span></span>  
  
## <a name="example-code"></a><span data-ttu-id="ea32e-108">코드 예</span><span class="sxs-lookup"><span data-stu-id="ea32e-108">Example Code</span></span>  
 [<span data-ttu-id="ea32e-109">MSReportServer_ConfigurationSetting 클래스</span><span class="sxs-lookup"><span data-stu-id="ea32e-109">MSReportServer_ConfigurationSetting Class</span></span>](msreportserver-configurationsetting-class.md)  
  
## <a name="remarks"></a><span data-ttu-id="ea32e-110">설명</span><span class="sxs-lookup"><span data-stu-id="ea32e-110">Remarks</span></span>  
 <span data-ttu-id="ea32e-111">값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ea32e-111">Values are:</span></span>  
  
-   <span data-ttu-id="ea32e-112">0: Windows 로그인</span><span class="sxs-lookup"><span data-stu-id="ea32e-112">0 for Windows login</span></span>  
  
-   <span data-ttu-id="ea32e-113">1: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인</span><span class="sxs-lookup"><span data-stu-id="ea32e-113">1 for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login</span></span>  
  
-   <span data-ttu-id="ea32e-114">2: 서비스로 로그인</span><span class="sxs-lookup"><span data-stu-id="ea32e-114">2 to log in as a service</span></span>  
  
 <span data-ttu-id="ea32e-115">0(Windows)을 지정하는 경우 [DatabaseLogonAccount](configurationsetting-property-databaselogonaccount.md) 속성의 값을 해당하는 Windows 사용자 계정으로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea32e-115">If you specify 0 (Windows), you must set the value in the [DatabaseLogonAccount](configurationsetting-property-databaselogonaccount.md) property to a corresponding a valid Windows user account.</span></span>  
  
 <span data-ttu-id="ea32e-116">1(SQL Server)을 지정하는 경우 [DatabaseLogonAccount](configurationsetting-property-databaselogonaccount.md) 값이 유효한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea32e-116">If you specify 1 (SQL Server), make sure the value of the [DatabaseLogonAccount](configurationsetting-property-databaselogonaccount.md) corresponds to a valid [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login.</span></span>  
  
 <span data-ttu-id="ea32e-117">2(Windows 서비스)를 지정하는 경우 보고서 서버는 [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] 계정과 Windows 서비스 계정을 사용하여 보고서 서버 데이터베이스에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="ea32e-117">If you specify 2 (Windows service), the report server uses an [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] account and the Windows service account to access the report server database.</span></span> <span data-ttu-id="ea32e-118">DatabaseLogonAccount 속성은 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea32e-118">The DatabaseLogonAccount property is ignored.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea32e-119">요구 사항</span><span class="sxs-lookup"><span data-stu-id="ea32e-119">Requirements</span></span>  
 <span data-ttu-id="ea32e-120">**네임스페이스:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea32e-120">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea32e-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ea32e-121">See Also</span></span>  
 [<span data-ttu-id="ea32e-122">MSReportServer_ConfigurationSetting 멤버</span><span class="sxs-lookup"><span data-stu-id="ea32e-122">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
