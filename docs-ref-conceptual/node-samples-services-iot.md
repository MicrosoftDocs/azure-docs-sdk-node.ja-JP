---
title: Node.js を使用した Azure メッセージングと IoT のサンプル コード
description: Node.js で Azure メッセージングと IoT を使用する方法を示すサンプル コード
author: rloutlaw
manager: routlaw
ms.devlang: nodejs
ms.topic: article
ms.service: azure-nodejs
ms.date: 06/17/2017
ms.author: routlaw
ms.openlocfilehash: 3169c3ef0d204e902db47d81ba02b638a5eb02f5
ms.sourcegitcommit: c332a32a1a850aa62405776bfe0e14251f722888
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
---
# <a name="sample-code-for-using-azure-messaging-and-iot-with-nodejs"></a><span data-ttu-id="2424d-103">Node.js で Azure メッセージングと IoT を使用するためのサンプル コード</span><span class="sxs-lookup"><span data-stu-id="2424d-103">Sample code for using Azure messaging and IoT with Node.js</span></span>

<span data-ttu-id="2424d-104">以下のサンプル コードには、Node.js で Azure メッセージングと IoT を使用する方法が紹介されています。</span><span class="sxs-lookup"><span data-stu-id="2424d-104">The following sample code illustrates using Azure messaging and IoT with Node.js</span></span>

<span data-ttu-id="2424d-105">他のタスクのコードが必要な場合は、[Azure Node.js サンプル](https://azure.microsoft.com/resources/samples/?term=nodejs)の完全な一覧を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2424d-105">If you need code for other tasks, you can browse the full list of [Azure Node.js samples](https://azure.microsoft.com/resources/samples/?term=nodejs).</span></span>

| | |
|---|---|
| <span data-ttu-id="2424d-106">**Azure IoT Hub**</span><span class="sxs-lookup"><span data-stu-id="2424d-106">**Azure IoT Hub**</span></span> ||
| [<span data-ttu-id="2424d-107">Azure IoT Hub ping</span><span class="sxs-lookup"><span data-stu-id="2424d-107">Azure IoT Hub ping</span></span>](https://github.com/Azure-Samples/iot-hub-node-ping) | <span data-ttu-id="2424d-108">Azure IoT Hub に対するデバイス接続の検証を支援する単純な ping ソリューション。</span><span class="sxs-lookup"><span data-stu-id="2424d-108">Simple ping solution to help validate a device connectivity to Azure IoT Hub.</span></span> |
| [<span data-ttu-id="2424d-109">Node.js を実行する Intel Edison からのデータに関して Azure IoT サービスが検出した振動の異常をツイートする</span><span class="sxs-lookup"><span data-stu-id="2424d-109">Tweet vibration anomalies detected by Azure IoT services on data from an Intel Edison running Node.js</span></span>](https://azure.microsoft.com/resources/samples/iot-hub-nodejs-intel-edison-vibration-anomaly-detection/) | <span data-ttu-id="2424d-110">Azure IoT Hub を使用した IoT プロジェクト。ノードを実行するデバイスから送信されたテレメトリ データを Azure IoT サービスによって解析する方法が紹介されています。</span><span class="sxs-lookup"><span data-stu-id="2424d-110">IoT project using Azure IoT Hub and showing a device running node to send telemetry data and that is analyzed by Azure IoT services.</span></span> |
| <span data-ttu-id="2424d-111">**Intel Edison IoT**</span><span class="sxs-lookup"><span data-stu-id="2424d-111">**Intel Edison IoT**</span></span> ||
| [<span data-ttu-id="2424d-112">Intel Edison Azure IoT スタート キットの概要</span><span class="sxs-lookup"><span data-stu-id="2424d-112">Get started with Intel Edison Azure IoT Starter Kit</span></span>](https://github.com/Azure-Samples/iot-hub-node-intel-edison-getstartedkit) | <span data-ttu-id="2424d-113">Azure IoT スタート キット (Intel Edison) を使って Azure IoT のデモンストレーションを行います。</span><span class="sxs-lookup"><span data-stu-id="2424d-113">Demonstrates Azure IoT using the Azure IoT Starter Kit - Intel Edison.</span></span> |
| <span data-ttu-id="2424d-114">**MQTT**</span><span class="sxs-lookup"><span data-stu-id="2424d-114">**MQTT**</span></span> ||
| [<span data-ttu-id="2424d-115">MQTT と HTTP のサンプル ゲートウェイ モジュール</span><span class="sxs-lookup"><span data-stu-id="2424d-115">Sample MQTT and HTTP Gateway modules</span></span>](https://github.com/Azure-Samples/iot-gateway-mqtt-http) | <span data-ttu-id="2424d-116">IoTHub スタイルの MQTT エンドポイントと HTTPS エンドポイントを公開することによってテレメトリのアップロードを (MQTT モジュールについては C2D メッセージングも) 行う 2 つのゲートウェイ モジュールを紹介します。</span><span class="sxs-lookup"><span data-stu-id="2424d-116">Provides two Gateway modules that expose IoTHub-style MQTT and HTTPS endpoints for telemetry upload, and in the case of MQTT module also C2D messaging.</span></span> |
| <span data-ttu-id="2424d-117">**Raspberry Pi**</span><span class="sxs-lookup"><span data-stu-id="2424d-117">**Raspberry Pi**</span></span> ||
| [<span data-ttu-id="2424d-118">Microsoft Azure IoT Raspberry Pi スタート キットの概要</span><span class="sxs-lookup"><span data-stu-id="2424d-118">Get Started with Microsoft Azure IoT Raspberry Pi Starter Kit</span></span>](https://github.com/Azure-Samples/iot-hub-node-raspberrypi-getting-started) | <span data-ttu-id="2424d-119">Azure IoT Raspberry Pi スタート キットの使用方法が紹介されています。</span><span class="sxs-lookup"><span data-stu-id="2424d-119">Illustrates using the Azure IoT Raspberry Pi Starter Kit.</span></span> |
| [<span data-ttu-id="2424d-120">Microsoft Azure IoT Raspberry Pi 3 スタート キットをリモート監視ソリューションに接続する</span><span class="sxs-lookup"><span data-stu-id="2424d-120">Connect your Microsoft Azure IoT Raspberry Pi 3 Starter Kit to the remote monitoring solution</span></span>](https://azure.microsoft.com/resources/samples/iot-remote-monitoring-node-raspberrypi-getstartedkit/) | <span data-ttu-id="2424d-121">Raspberry Pi 3 デバイスを Azure IoT Suite のリモート監視ソリューションに接続する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2424d-121">Learn how to connect a Raspberry Pi 3 device to the Azure IoT Suite remote monitoring solution.</span></span> |
