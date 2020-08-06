---
title: 렌더링 확장 프로그램 제거 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- deleting rendering extensions
- removing rendering extensions
- rendering extensions [Reporting Services], removing
ms.assetid: 2abfebfb-065f-45cc-a904-c914394cf900
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 77a8a9ac44b35f338f978913985617e4f264ddb7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651526"
---
# <a name="removing-a-rendering-extension"></a><span data-ttu-id="fbbb0-102">렌더링 확장 프로그램 제거</span><span class="sxs-lookup"><span data-stu-id="fbbb0-102">Removing a Rendering Extension</span></span>
  <span data-ttu-id="fbbb0-103">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]렌더링 확장 프로그램을 제거 하려면 `Extension` **%ProgramFiles%\Microsoft SQL Server \ MSRS10_50에 있는 rsreportserver.config 파일에서 렌더링 확장 프로그램에 대 한 요소를 제거 하면 됩니다. \<Instance Name> \Reporting Services\ReportServer** 폴더</span><span class="sxs-lookup"><span data-stu-id="fbbb0-103">To remove a [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] rendering extension, simply remove the `Extension` element for your rendering extension from the rsreportserver.config file, located in **%ProgramFiles%\Microsoft SQL Server\MSRS10_50.\<Instance Name>\Reporting Services\ReportServer** folder.</span></span> <span data-ttu-id="fbbb0-104">보고서 디자이너 및 보고서 서버에 대 한 항목을 만든 경우 `Extension` [Rsreportdesigner.config 구성 파일](../../report-server/rsreportdesigner-configuration-file.md) 에서도 요소를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="fbbb0-104">If you made entries for a Report Designer as well as a report server, remove the `Extension` element from the [RSReportDesigner Configuration File](../../report-server/rsreportdesigner-configuration-file.md) as well.</span></span> <span data-ttu-id="fbbb0-105">구성 정보를 제거한 후에는 구성 요소에서 렌더링 확장 프로그램을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fbbb0-105">After the configuration information is removed, the rendering extension is no longer available to the component.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbbb0-106">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fbbb0-106">See Also</span></span>  
 <span data-ttu-id="fbbb0-107">[Reporting Services 구성 파일](../../report-server/reporting-services-configuration-files.md) </span><span class="sxs-lookup"><span data-stu-id="fbbb0-107">[Reporting Services Configuration Files](../../report-server/reporting-services-configuration-files.md) </span></span>  
 <span data-ttu-id="fbbb0-108">[렌더링 확장 프로그램 구현](implementing-a-rendering-extension.md) </span><span class="sxs-lookup"><span data-stu-id="fbbb0-108">[Implementing a Rendering Extension](implementing-a-rendering-extension.md) </span></span>  
 <span data-ttu-id="fbbb0-109">[렌더링 확장 프로그램 개요](rendering-extensions-overview.md) </span><span class="sxs-lookup"><span data-stu-id="fbbb0-109">[Rendering Extensions Overview](rendering-extensions-overview.md) </span></span>  
 <span data-ttu-id="fbbb0-110">[IRenderingExtension 인터페이스 구현](implementing-the-irenderingextension-interface.md) </span><span class="sxs-lookup"><span data-stu-id="fbbb0-110">[Implementing the IRenderingExtension Interface](implementing-the-irenderingextension-interface.md) </span></span>  
 <span data-ttu-id="fbbb0-111">[확장에 대한 보안 고려 사항](../security-considerations-for-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="fbbb0-111">[Security Considerations for Extensions](../security-considerations-for-extensions.md) </span></span>  
 [<span data-ttu-id="fbbb0-112">렌더링 확장 프로그램 배포</span><span class="sxs-lookup"><span data-stu-id="fbbb0-112">Deploying a Rendering Extension</span></span>](deploying-a-rendering-extension.md)  
  
  
