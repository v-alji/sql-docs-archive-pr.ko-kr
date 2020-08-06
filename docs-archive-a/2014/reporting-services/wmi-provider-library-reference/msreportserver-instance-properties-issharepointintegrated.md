---
title: IsSharePointIntegrated 속성(WMI MSReportServer_Instance) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- IsSharePointIntegrated property
ms.assetid: e21d00ad-5d9a-4290-8d74-7eeeda39e1ed
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d0c92ebe586d37053b47f90ca98c31b3068a7b91
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649891"
---
# <a name="issharepointintegrated-property-wmi-msreportserver_instance"></a><span data-ttu-id="dcf9b-102">IsSharePointIntegrated 속성(WMI MSReportServer_Instance)</span><span class="sxs-lookup"><span data-stu-id="dcf9b-102">IsSharePointIntegrated Property (WMI MSReportServer_Instance)</span></span>
  <span data-ttu-id="dcf9b-103">보고서 서버가 SharePoint 통합 모드에 있는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="dcf9b-103">Specifies whether the report server is in SharePoint integrated mode.</span></span> <span data-ttu-id="dcf9b-104">SharePoint 모드에서는 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 인스턴스가 SharePoint 공유 서비스이며 WMI 공급자를 통해 제어되지 않으므로 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]부터는 이 속성이 항상 `False`를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="dcf9b-104">Beginning in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], this property always returns `False` because in SharePoint mode, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instances are SharePoint shared services and are not controlled by WMI providers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcf9b-105">구문</span><span class="sxs-lookup"><span data-stu-id="dcf9b-105">Syntax</span></span>  
  
```vb  
Public Dim IsSharePointIntegrated As Boolean  
```  
  
```csharp  
public Boolean IsSharePointIntegrated;  
```  
  
## <a name="property-values"></a><span data-ttu-id="dcf9b-106">속성 값</span><span class="sxs-lookup"><span data-stu-id="dcf9b-106">Property Values</span></span>  
 <span data-ttu-id="dcf9b-107">보고서 서버가 SharePoint 통합 모드에 있는지 여부를 나타내는 `Boolean` 값입니다.</span><span class="sxs-lookup"><span data-stu-id="dcf9b-107">A `Boolean` value that indicates whether the report server is in SharePoint integrated mode.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dcf9b-108">요구 사항</span><span class="sxs-lookup"><span data-stu-id="dcf9b-108">Requirements</span></span>  
 <span data-ttu-id="dcf9b-109">**네임스페이스:** [!INCLUDE[ssRSWMInmspc](../../includes/ssrswminmspc-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dcf9b-109">**Namespace:** [!INCLUDE[ssRSWMInmspc](../../includes/ssrswminmspc-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcf9b-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="dcf9b-110">See Also</span></span>  
 <span data-ttu-id="dcf9b-111">[MSReportServer_Instance 멤버](msreportserver-instance-members.md) </span><span class="sxs-lookup"><span data-stu-id="dcf9b-111">[MSReportServer_Instance Members](msreportserver-instance-members.md) </span></span>  
 [<span data-ttu-id="dcf9b-112">MSReportServer_ConfigurationSetting 클래스</span><span class="sxs-lookup"><span data-stu-id="dcf9b-112">MSReportServer_ConfigurationSetting Class</span></span>](msreportserver-configurationsetting-class.md)  
  
  
