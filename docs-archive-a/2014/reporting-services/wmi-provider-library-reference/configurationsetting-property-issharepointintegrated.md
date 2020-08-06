---
title: IsSharePointIntegrated 속성(WMI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- IsSharePointIntegrated property
ms.assetid: c548fed8-5e04-4faf-8b10-b37c86178056
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a1f3f38c23546ddf4dfb52c2a3af7c122af10cbd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653196"
---
# <a name="issharepointintegrated-property-wmi"></a><span data-ttu-id="f4f7e-102">IsSharePointIntegrated 속성(WMI)</span><span class="sxs-lookup"><span data-stu-id="f4f7e-102">IsSharePointIntegrated Property (WMI)</span></span>
  <span data-ttu-id="f4f7e-103">보고서 서버가 SharePoint 통합 모드에 있는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f4f7e-103">Specifies whether the report server is in SharePoint integrated mode.</span></span> <span data-ttu-id="f4f7e-104">SharePoint 모드에서는 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 인스턴스가 SharePoint 공유 서비스이며 WMI 공급자를 통해 제어되지 않으므로 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]부터는 이 속성이 항상 `False`를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f4f7e-104">Beginning in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], this property always returns `False` because in SharePoint mode, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instances are SharePoint shared services and are not controlled by WMI providers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4f7e-105">구문</span><span class="sxs-lookup"><span data-stu-id="f4f7e-105">Syntax</span></span>  
  
```vb  
Public Dim IsSharePointIntegrated As Boolean  
```  
  
```csharp  
public Boolean IsSharePointIntegrated;  
```  
  
## <a name="property-values"></a><span data-ttu-id="f4f7e-106">속성 값</span><span class="sxs-lookup"><span data-stu-id="f4f7e-106">Property Values</span></span>  
 <span data-ttu-id="f4f7e-107">보고서 서버가 SharePoint 통합 모드에 있는지 여부를 나타내는 `Boolean` 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="f4f7e-107">A `Boolean` object that indicates whether the report server is in SharePoint integrated mode.</span></span>  
  
## <a name="example-code"></a><span data-ttu-id="f4f7e-108">코드 예</span><span class="sxs-lookup"><span data-stu-id="f4f7e-108">Example Code</span></span>  
 [<span data-ttu-id="f4f7e-109">MSReportServer_ConfigurationSetting 클래스</span><span class="sxs-lookup"><span data-stu-id="f4f7e-109">MSReportServer_ConfigurationSetting Class</span></span>](msreportserver-configurationsetting-class.md)  
  
## <a name="requirements"></a><span data-ttu-id="f4f7e-110">요구 사항</span><span class="sxs-lookup"><span data-stu-id="f4f7e-110">Requirements</span></span>  
 <span data-ttu-id="f4f7e-111">**네임스페이스:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4f7e-111">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4f7e-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f4f7e-112">See Also</span></span>  
 [<span data-ttu-id="f4f7e-113">MSReportServer_ConfigurationSetting 멤버</span><span class="sxs-lookup"><span data-stu-id="f4f7e-113">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
