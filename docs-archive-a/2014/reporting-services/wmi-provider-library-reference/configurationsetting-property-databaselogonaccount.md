---
title: DatabaseLogonAccount 속성(WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- DatabaseLogonAccount
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- DatabaseLogonAccount property
ms.assetid: 55f2863f-1ac1-4519-b512-e7f11c0ea5ea
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6f9e844ff1d1447bd5abfefad8e82939575c7f47
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737678"
---
# <a name="databaselogonaccount-property-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="46a11-102">DatabaseLogonAccount 속성(WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="46a11-102">DatabaseLogonAccount Property (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="46a11-103">보고서 서버에서 보고서 서버 데이터베이스에 연결할 때 사용하는 로그온 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="46a11-103">Specifies the logon account that the report server uses when connecting to the report server database.</span></span> <span data-ttu-id="46a11-104">읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="46a11-104">Read only.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46a11-105">구문</span><span class="sxs-lookup"><span data-stu-id="46a11-105">Syntax</span></span>  
  
```vb  
Public Dim DatabaseLogonAccount As String  
```  
  
```csharp  
public string DatabaseLogonAccount;  
```  
  
## <a name="property-values"></a><span data-ttu-id="46a11-106">속성 값</span><span class="sxs-lookup"><span data-stu-id="46a11-106">Property Values</span></span>  
 <span data-ttu-id="46a11-107">로그온 계정 이름을 나타내는 `String` 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="46a11-107">A `String` object that represents the logon account name.</span></span>  
  
## <a name="example-code"></a><span data-ttu-id="46a11-108">코드 예</span><span class="sxs-lookup"><span data-stu-id="46a11-108">Example Code</span></span>  
 [<span data-ttu-id="46a11-109">MSReportServer_ConfigurationSetting 클래스</span><span class="sxs-lookup"><span data-stu-id="46a11-109">MSReportServer_ConfigurationSetting Class</span></span>](msreportserver-configurationsetting-class.md)  
  
## <a name="remarks"></a><span data-ttu-id="46a11-110">설명</span><span class="sxs-lookup"><span data-stu-id="46a11-110">Remarks</span></span>  
 <span data-ttu-id="46a11-111">이 속성의 유효 값은 [DatabaseLogonType](configurationsetting-property-databaselogontype.md) 속성 값에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="46a11-111">Valid values for this property will vary depending on the value of the [DatabaseLogonType](configurationsetting-property-databaselogontype.md) property.</span></span>  
  
 <span data-ttu-id="46a11-112">[Databaselogontype](configurationsetting-property-databaselogontype.md) 속성이로 설정 된 경우이 속성은 무시 됩니다 `2 (Service)` .</span><span class="sxs-lookup"><span data-stu-id="46a11-112">This property is ignored if the [DatabaseLogonType](configurationsetting-property-databaselogontype.md) property is set to `2 (Service)`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46a11-113">요구 사항</span><span class="sxs-lookup"><span data-stu-id="46a11-113">Requirements</span></span>  
 <span data-ttu-id="46a11-114">**네임스페이스:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46a11-114">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46a11-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="46a11-115">See Also</span></span>  
 [<span data-ttu-id="46a11-116">MSReportServer_ConfigurationSetting 멤버</span><span class="sxs-lookup"><span data-stu-id="46a11-116">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
