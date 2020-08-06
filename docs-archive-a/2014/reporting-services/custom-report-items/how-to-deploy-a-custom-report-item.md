---
title: '방법: 사용자 지정 보고서 항목 배포 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- custom report items, deploying
ms.assetid: 80e97b0d-e355-4240-aebd-08cbc84089ed
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 66519610526478caadeb41b48c9823414e88d5d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741632"
---
# <a name="how-to-deploy-a-custom-report-item"></a><span data-ttu-id="1bb6c-102">방법: 사용자 지정 보고서 항목 배포</span><span class="sxs-lookup"><span data-stu-id="1bb6c-102">How to: Deploy a Custom Report Item</span></span>
  <span data-ttu-id="1bb6c-103">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]에서 사용자 지정 보고서 항목을 배포하려면 보고서 서버 구성 파일을 수정하고 디자인 타임 및 런타임 구성 요소 어셈블리를 보고서 디자이너와 보고서 서버 양쪽의 적절한 애플리케이션 폴더로 복사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1bb6c-103">To deploy a custom report item in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], you must modify the report server configuration files and copy the design-time and run-time component assemblies into the appropriate application folders for both Report Designer and the report server.</span></span>  
  
### <a name="to-deploy-a-custom-report-item"></a><span data-ttu-id="1bb6c-104">사용자 지정 보고서 항목을 배포하려면</span><span class="sxs-lookup"><span data-stu-id="1bb6c-104">To deploy a custom report item</span></span>  
  
1.  <span data-ttu-id="1bb6c-105">Rsreportdesigner.config 파일을 편집하여 디자이너에서 사용하도록 사용자 지정 보고서 항목 런타임 및 디자인 타임 구성 요소를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="1bb6c-105">Edit the Rsreportdesigner.config file to configure the custom report item run-time and design-time components for use in the designer.</span></span> <span data-ttu-id="1bb6c-106">`ReportItemName` 항목이 `CustomReportItemAttribute` 클래스에 사용되는 `CustomReportItemDesigner` 특성과 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1bb6c-106">Note that the `ReportItemName` entry must match the `CustomReportItemAttribute` attribute used in your `CustomReportItemDesigner` class.</span></span> <span data-ttu-id="1bb6c-107">예:</span><span class="sxs-lookup"><span data-stu-id="1bb6c-107">For example:</span></span>  
  
    ```  
    <ReportItems>  
       <ReportItem Name="Polygons" Type="PolygonsCRI.PolygonsCRI,PolygonsCRI"/>  
    </ReportItems>  
    <ReportItemDesigner>  
       <ReportItem Name="Polygons" Type="PolygonsCRI.PolygonsDesigner, PolygonsDesigner" />  
    </ReportItemDesigner>  
    <ReportItemConverter>  
       <Converter Source="Chart" Target="Polygons" Type="PolygonsCRI.PolygonsConverter, PolygonsDesigner" />  
    </ReportItemConverter>  
    ```  
  
2.  <span data-ttu-id="1bb6c-108">Rsreportserver.config 파일을 편집하여 사용자 지정 보고서 항목 런타임 구성 요소를 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="1bb6c-108">Edit the Rsreportserver.config file to register the custom report item run-time component.</span></span> <span data-ttu-id="1bb6c-109">다음은 그 예입니다.</span><span class="sxs-lookup"><span data-stu-id="1bb6c-109">For example:</span></span>  
  
    ```  
    <ReportItems>  
       <ReportItem Name="Polygons" Type="PolygonsCRI.PolygonsCRI,PolygonsCRI"/>  
    </ReportItems>  
    ```  
  
3.  <span data-ttu-id="1bb6c-110">Rsssrvpolicy.config 파일을 편집하여 사용자 지정 보고서 항목에 적절한 권한을 부여하는 `CodeGroup`을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="1bb6c-110">Edit the Rsssrvpolicy.config file to add a `CodeGroup` that grants the proper permissions to the custom report item.</span></span> <span data-ttu-id="1bb6c-111">다음은 그 예입니다.</span><span class="sxs-lookup"><span data-stu-id="1bb6c-111">For example:</span></span>  
  
    ```  
    <CodeGroup   
       class="UnionCodeGroup"   
       version="1"   
       PermissionSetName="FullTrust"  
       Description="This code group grants MyCustomReportItem.dll FullTrust permission. ">  
       <IMembershipCondition   
          class="UrlMembershipCondition"  
          version="1"  
       Url="C:\Program Files\Microsoft SQL Server\ MSRS10_50.SQLSERVER\Reporting Services\ReportServer\bin\MyCustomReportItem.dll" />  
    </CodeGroup>  
    ```  
  
4.  <span data-ttu-id="1bb6c-112">사용자 지정 보고서 항목 런타임 구성 요소 DLL을 %ProgramFiles%\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies 및 \Program Files\Microsoft SQL Server\MSRS10_50.SQLSERVER\Reporting Services\ReportServer\bin 디렉터리로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="1bb6c-112">Copy the custom report item run-time component DLL to the %ProgramFiles%\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies and \Program Files\Microsoft SQL Server\MSRS10_50.SQLSERVER\Reporting Services\ReportServer\bin directories.</span></span>  
  
5.  <span data-ttu-id="1bb6c-113">사용자 지정 보고서 항목 디자인 타임 구성 요소 DLL을 %ProgramFiles%\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies 디렉터리로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="1bb6c-113">Copy the custom report item design-time component DLL to the %ProgramFiles%\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bb6c-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1bb6c-114">See Also</span></span>  
 <span data-ttu-id="1bb6c-115">[Reporting Services 구성 파일](../report-server/reporting-services-configuration-files.md) </span><span class="sxs-lookup"><span data-stu-id="1bb6c-115">[Reporting Services Configuration Files](../report-server/reporting-services-configuration-files.md) </span></span>  
 [<span data-ttu-id="1bb6c-116">사용자 지정 보고서 항목 클래스 라이브러리</span><span class="sxs-lookup"><span data-stu-id="1bb6c-116">Custom Report Item Class Libraries</span></span>](custom-report-item-class-libraries.md)  
  
  
