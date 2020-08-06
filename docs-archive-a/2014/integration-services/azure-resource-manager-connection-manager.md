---
title: Azure Resource Manager 연결 관리자 | Microsoft Docs
ms.custom: ''
ms.date: 02/28/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.AFPARMCM.F1
- SQL11.DTS.DESIGNER.AFPARMCM.F1
ms.assetid: a2380258-0418-4a8c-a731-5071a44ddf1e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1dce4def11f14072295dbf3cde9d5ab77304fe74
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651873"
---
# <a name="azure-resource-manager-connection-manager"></a><span data-ttu-id="d1ab9-102">Azure Resource Manager 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="d1ab9-102">Azure Resource Manager Connection Manager</span></span>
<span data-ttu-id="d1ab9-103">**Azure Resource Manager 연결 관리자**를 통해 SSIS 패키지는 [서비스 사용자](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal)를 사용하여 Azure 리소스를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1ab9-103">The **Azure Resource Manager Connection Manager** enables an SSIS package to manage Azure resources using a [service principal](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal).</span></span>

<span data-ttu-id="d1ab9-104">**Azure Resource Manager 연결 관리자**를 만들고 구성하려면 다음 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ab9-104">To create and configure an **Azure Resource Manager Connection Manager**, follow the steps below:</span></span>

1. <span data-ttu-id="d1ab9-105">**SSIS 연결 관리자 추가** 대화 상자에서 **AzureResourceManager**를 선택하고 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ab9-105">In the **Add SSIS Connection Manager** dialog box, select **AzureResourceManager**, and click **Add**.</span></span>
2. <span data-ttu-id="d1ab9-106">**Azure Resource Manager 연결 관리자 편집기** 대화 상자에서 서비스 사용자에 대한 **애플리케이션 ID**, **애플리케이션 키** 및 **테넌트 ID**를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ab9-106">In the **Azure Resource Manager Connection Manager Editor** dialog box, specify the **Application ID**, **Application Key**, and **Tenant ID** for the service principal.</span></span> <span data-ttu-id="d1ab9-107">이러한 속성에 대한 자세한 내용은 [이](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal) 문서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d1ab9-107">For details about these properties, please refer to [this](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal) article.</span></span>
3. <span data-ttu-id="d1ab9-108">**확인** 을 클릭하여 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="d1ab9-108">Click **OK** to close the dialog box.</span></span>
4. <span data-ttu-id="d1ab9-109">작성한 연결 관리자의 속성은 **속성** 창에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1ab9-109">You can see the properties of the connection manager you created in the **Properties** window.</span></span>
