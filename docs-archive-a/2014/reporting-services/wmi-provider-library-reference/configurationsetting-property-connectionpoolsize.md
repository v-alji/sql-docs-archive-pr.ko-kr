---
title: ConnectionPoolSize 속성(WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- ConnectionPoolSize
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- ConnectionPoolSize property
ms.assetid: b80c8e5d-b725-4fe4-aec6-02fb18ec4434
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 24a180fde90ff406d40a0f0c89bf82dfe5138b88
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737683"
---
# <a name="connectionpoolsize-property-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="f0e4e-102">ConnectionPoolSize 속성(WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="f0e4e-102">ConnectionPoolSize Property (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="f0e4e-103">보고서 서버 데이터베이스를 호스팅하는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스와 통신하기 위해 보고서 서버에서 사용하는 연결 풀 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="f0e4e-103">The connection pool size used by the report server to communicate with the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance that hosts the report server database.</span></span> <span data-ttu-id="f0e4e-104">읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="f0e4e-104">Read-only.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0e4e-105">구문</span><span class="sxs-lookup"><span data-stu-id="f0e4e-105">Syntax</span></span>  
  
```vb  
Public Dim ConnectionPoolSize As UInt32  
```  
  
```csharp  
public UInt32 ConnectionPoolSize;  
```  
  
## <a name="property-values"></a><span data-ttu-id="f0e4e-106">속성 값</span><span class="sxs-lookup"><span data-stu-id="f0e4e-106">Property Values</span></span>  
 <span data-ttu-id="f0e4e-107">의 값을 반환 하는 읽기 전용 **정수** 개체입니다 `768` .</span><span class="sxs-lookup"><span data-stu-id="f0e4e-107">A read-only **integer** object that returns a value of `768`.</span></span>  
  
## <a name="example-code"></a><span data-ttu-id="f0e4e-108">코드 예</span><span class="sxs-lookup"><span data-stu-id="f0e4e-108">Example Code</span></span>  
 [<span data-ttu-id="f0e4e-109">MSReportServer_ConfigurationSetting 클래스</span><span class="sxs-lookup"><span data-stu-id="f0e4e-109">MSReportServer_ConfigurationSetting Class</span></span>](msreportserver-configurationsetting-class.md)  
  
## <a name="requirements"></a><span data-ttu-id="f0e4e-110">요구 사항</span><span class="sxs-lookup"><span data-stu-id="f0e4e-110">Requirements</span></span>  
 <span data-ttu-id="f0e4e-111">**네임스페이스:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0e4e-111">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0e4e-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f0e4e-112">See Also</span></span>  
 [<span data-ttu-id="f0e4e-113">MSReportServer_ConfigurationSetting 멤버</span><span class="sxs-lookup"><span data-stu-id="f0e4e-113">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
