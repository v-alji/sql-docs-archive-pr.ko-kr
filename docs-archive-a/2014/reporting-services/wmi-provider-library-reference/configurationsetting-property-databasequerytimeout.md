---
title: DatabaseQueryTimeout 속성(WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- DatabaseQueryTimeout Property
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- DatabaseQueryTimeout property
ms.assetid: 96faed97-9799-4bbf-a66f-fdd532d3eace
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2e92e3e0f6752ea99fe89c962ebe96e343c0195b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737659"
---
# <a name="databasequerytimeout-property-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="10cc2-102">DatabaseQueryTimeout 속성(WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="10cc2-102">DatabaseQueryTimeout Property (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="10cc2-103">보고서 서버에서 명령이 실패하거나 수행 시간이 너무 오래 걸린다고 간주하기 전에 경과해야 하는 시간(초)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="10cc2-103">Specifies the number of seconds that must elapse before the report server assumes the command failed or took too much time to perform.</span></span> <span data-ttu-id="10cc2-104">보고서 서버는 보고서의 데이터 원본이 아닌 SQL 카탈로그에 대해 쿼리 시간을 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="10cc2-104">The report server is timing the querying against the SQL catalog, not a data source for the report.</span></span> <span data-ttu-id="10cc2-105">읽기/쓰기입니다.</span><span class="sxs-lookup"><span data-stu-id="10cc2-105">Read/write.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10cc2-106">구문</span><span class="sxs-lookup"><span data-stu-id="10cc2-106">Syntax</span></span>  
  
```vb  
Public Dim DatabaseQueryTimeout As UInt32  
```  
  
```csharp  
public UInt32 DatabaseQueryTimeout;  
```  
  
## <a name="property-values"></a><span data-ttu-id="10cc2-107">속성 값</span><span class="sxs-lookup"><span data-stu-id="10cc2-107">Property Values</span></span>  
 <span data-ttu-id="10cc2-108">쿼리를 실행할 수 있는 시간(초)을 나타내는 부호 없는 32비트 `integer` 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="10cc2-108">A 32-bit unsigned `integer` object that represents the number of seconds that the query is allowed to run.</span></span>  
  
## <a name="example-code"></a><span data-ttu-id="10cc2-109">코드 예</span><span class="sxs-lookup"><span data-stu-id="10cc2-109">Example Code</span></span>  
 [<span data-ttu-id="10cc2-110">MSReportServer_ConfigurationSetting 클래스</span><span class="sxs-lookup"><span data-stu-id="10cc2-110">MSReportServer_ConfigurationSetting Class</span></span>](msreportserver-configurationsetting-class.md)  
  
## <a name="requirements"></a><span data-ttu-id="10cc2-111">요구 사항</span><span class="sxs-lookup"><span data-stu-id="10cc2-111">Requirements</span></span>  
 <span data-ttu-id="10cc2-112">**네임스페이스:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10cc2-112">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10cc2-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="10cc2-113">See Also</span></span>  
 [<span data-ttu-id="10cc2-114">MSReportServer_ConfigurationSetting 멤버</span><span class="sxs-lookup"><span data-stu-id="10cc2-114">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
