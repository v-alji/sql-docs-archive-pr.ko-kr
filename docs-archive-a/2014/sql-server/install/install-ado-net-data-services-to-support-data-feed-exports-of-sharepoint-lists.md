---
title: ADO.NET Data Services를 설치 하 여 SharePoint 목록의 데이터 피드 내보내기를 지원 합니다. | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: f32527ae-f623-4e08-adfb-6d3262f5c2ac
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: fb47804daee38427f48baefdf3997edda5fb90b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648768"
---
# <a name="install-adonet-data-services-to-support-data-feed-exports-of-sharepoint-lists"></a><span data-ttu-id="64e0b-102">ADO.NET Data Services를 설치하여 SharePoint 목록의 데이터 피드 내보내기 지원</span><span class="sxs-lookup"><span data-stu-id="64e0b-102">Install ADO.NET Data Services to support data feed exports of SharePoint lists</span></span>
  <span data-ttu-id="64e0b-103">SharePoint 목록의 데이터 피드 내보내기를 수행하려면 ADO.NET Data Services가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="64e0b-103">ADO.NET Data Services is required for a data feed export of SharePoint lists.</span></span> <span data-ttu-id="64e0b-104">이 구성 요소는 SharePoint 2010의 SharePoint 필수 구성 요소 설치 관리자 프로그램에 포함되어 있지 않으므로 수동으로 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="64e0b-104">SharePoint 2010 does not include this component in the SharePoint Prerequisite Installer program, so you must install it manually.</span></span>  
  
 <span data-ttu-id="64e0b-105">이 필수 구성 요소가 없는 경우 데이터 피드로 내보내진 SharePoint 목록을 사용하려고 시도하면 다음 오류가 표시됩니다. "보안상의 이유로 이 XML 문서에는 DTD가 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="64e0b-105">Without this prerequisite, you will get the following error when you attempt to use a SharePoint list that was exported as a data feed: "For security reasons DTD is prohibited in this XML document.</span></span> <span data-ttu-id="64e0b-106">DTD 처리를 활성화하려면 XmlReaderSettings의 ProhibitDtd 속성을 false로 설정하고 이 설정을 XmlReader.Create 메서드로 전달합니다."</span><span class="sxs-lookup"><span data-stu-id="64e0b-106">To enable DTD processing set the ProhibitDtd property on XmlReaderSettings to false and pass the settings into XmlReader.Create method."</span></span>  
  
 <span data-ttu-id="64e0b-107">다음 지침에 따라 목록을 데이터 피드로 내보내도록 허용할 모든 SharePoint 서버에 ADO.NET Data Services를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="64e0b-107">Use the following instructions to install ADO.NET Data Services on every SharePoint server for which you want to allow lists to be exported as data feeds.</span></span>  
  
### <a name="download-and-install-adonet-data-services"></a><span data-ttu-id="64e0b-108">ADO.NET Data Services 다운로드 및 설치</span><span class="sxs-lookup"><span data-stu-id="64e0b-108">Download and install ADO.NET Data Services</span></span>  
  
1.  <span data-ttu-id="64e0b-109">SharePoint 2010의 하드웨어 및 소프트웨어 요구 사항 설명서를 보려면 [하드웨어 및 소프트웨어 요구 사항(SharePoint Server 2010)](https://go.microsoft.com/fwlink/?LinkId=169734)으로 이동하십시오.</span><span class="sxs-lookup"><span data-stu-id="64e0b-109">Go to the hardware and software requirements documentation for SharePoint 2010, [Hardware and Software Requirements (SharePoint 2010)](https://go.microsoft.com/fwlink/?LinkId=169734)</span></span>  
  
2.  <span data-ttu-id="64e0b-110">**적용 가능한 소프트웨어에 대한 액세스**에서 현재 사용 중인 운영 체제(Windows Server 2008 SP2 또는 Windows Server 2008 R2)에 맞는 ADO.NET Data Services 3.5의 링크를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="64e0b-110">In **Access to applicable software**, find the link for ADO.NET Data Services 3.5 that corresponds to the operating system you are using (either Windows Server 2008 SP2 or Windows Server 2008 R2).</span></span>  
  
3.  <span data-ttu-id="64e0b-111">링크를 클릭하여 서비스를 설치하는 설치 프로그램을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="64e0b-111">Click the link and run the setup program that installs the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64e0b-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="64e0b-112">See Also</span></span>  
 [<span data-ttu-id="64e0b-113">SharePoint 2010용 PowerPivot 설치</span><span class="sxs-lookup"><span data-stu-id="64e0b-113">PowerPivot for SharePoint 2010 Installation</span></span>](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
  
